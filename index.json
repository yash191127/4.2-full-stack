const express = require('express')
const app = express()
app.use(express.json())

let cards = [
  { id: 1, suit: 'Hearts', value: 'Ace' },
  { id: 2, suit: 'Spades', value: 'King' },
  { id: 3, suit: 'Diamonds', value: 'Queen' }
]

app.get('/cards', (req, res) => {
  res.json(cards)
})

app.get('/cards/:id', (req, res) => {
  const card = cards.find(c => c.id === parseInt(req.params.id))
  if (!card) return res.status(404).json({ message: 'Card not found' })
  res.json(card)
})

app.post('/cards', (req, res) => {
  const newCard = {
    id: cards.length ? cards[cards.length - 1].id + 1 : 1,
    suit: req.body.suit,
    value: req.body.value
  }
  cards.push(newCard)
  res.status(201).json(newCard)
})

app.delete('/cards/:id', (req, res) => {
  const index = cards.findIndex(c => c.id === parseInt(req.params.id))
  if (index === -1) return res.status(404).json({ message: 'Card not found' })
  const deleted = cards.splice(index, 1)
  res.json({ message: `Card with id ${req.params.id} deleted`, card: deleted[0] })
})

app.listen(3000, () => {
  console.log('Server running on port 3000')
})
