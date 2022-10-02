# Desafio-estrutura-de-dados
class No:
  #declaração do construtor
  def __init__(self, valor):
    self.valor=valor
    self.esquerda=None
    self.direita=None

    def mostra_no(self):
      print(self.valor)

class ArvoreBinariaBusca:
  def __init__(self):
    self.raiz=None
    self.ligacoes=[]

  def inserir(self, valor):
    novoNo=No(valor)
    #se a arvore estiver vazia
    if self.raiz==None:
      self.raiz=novoNo
    else:
      atual=self.raiz
      while True:
        pai=atual
        #esquerda
        if valor < atual.valor:
          atual=atual.esquerda
          if atual==None:
            pai.esquerda=novoNo
            return
        #direita
        else:
          atual=atual.direita
          if atual==None:
            pai.direita=novoNo
            return
            
  def excluir(self, valor):
    if self.raiz==None:
      print("Arvore está vazia")
      return
    #encontrar o no
      atual=self.raiz
      pai=self.raiz
      e_esquerda=True
      while atual.valor != valor:
        pai=atual
        #esquerda
        if valor<atual.valor:
          e_esquerda=True
          atual=atual.esquerda
        #direita
        if valor>atual.valor:
          e_esquerda=False
          atual=atual.direita
        if atual==None:
          return false
        
     

  def pesquisar(self, valor):
    atual=self.raiz
    while atual.valor != valor:
      if valor < atual.valor:
        atual=atual.esquerda
      else:
        atual=atual.direita
      if atual == None:
        return None
    return atual
  #pre-ordem: raiz, esquerda, direita
  def pre_ordem(self, no):
    if no != None:
      print(no.valor)
      self.pre_ordem(no.esquerda)
      self.pre_ordem(no.direita)
#ordem: esquerda, raiz, direita
  def em_ordem(self, no):
    if no != None:
      self.em_ordem(no.esquerda)
      print(no.valor)
      self.em_ordem(no.direita)
#pós-ordem: esqu4erda, direita, raiz
  def pos_ordem(self, no):
    if no != None:
      self.pos_ordem(no.esquerda)
      self.pos_ordem(no.direita)
      print(no.valor)


tree=ArvoreBinariaBusca()
tree.inserir(40)
tree.inserir(20)
tree.inserir(10)
tree.inserir(30)
tree.inserir(60)
tree.inserir(50)
tree.inserir(70)

print("Busca de nó na arvore")
print(tree.pesquisar(4))
print("Visualização pre-ordem")
print(tree.pre_ordem(tree.raiz))
print("Visualização em ordem")
print(tree.em_ordem(tree.raiz))
print("Visualização pos-ordem")
print(tree.pos_ordem(tree.raiz))

print("No esquerda:", tree.raiz.esquerda.valor)
print("No direita:", tree.raiz.direita.valor)
print("No raiz:", tree.raiz.valor)
