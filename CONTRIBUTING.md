# 🚀 Guia de Contribuição - uniarpdev

Este documento define o padrão de colaboração para todos os repositórios da organização **uniarpdev**. Como trabalhamos com bibliotecas compartilhadas (NuGet), a integridade da branch `main` e o versionamento correto são críticos.

---

## 1. Regra Fundamental
**É estritamente proibido realizar `push` diretamente na branch `main`.** Mesmo que o sistema não bloqueie a ação no plano gratuito, todos os colaboradores devem utilizar o fluxo de Pull Requests para garantir a revisão de código.

---

## 2. Fluxo de Trabalho (Git Flow Simplificado)

O fluxo padrão para qualquer alteração (correção ou nova funcionalidade) segue estes passos:

### A. Sincronização
Garanta que sua branch local está atualizada antes de começar:
* `git checkout main`
* `git pull origin main`

### B. Criação de Branch
Crie uma branch de funcionalidade com nome semântico:
* `git checkout -b feature/nome-da-mudanca`

### C. Alteração de Versão (Obrigatório)
Antes de finalizar, abra o arquivo `.csproj` do projeto alterado e incremente a tag `<Version>` seguindo o [Semantic Versioning](https://semver.org/):
* **Patch (1.0.x):** Correções de bugs.
* **Minor (1.x.0):** Novas funcionalidades que não quebram compatibilidade.
* **Major (x.0.0):** Alterações que quebram a compatibilidade atual.

### D. Envio
Realize o commit e suba a branch:
* `git add .`
* `git commit -m "feat: descrição curta da mudança"`
* `git push origin feature/nome-da-mudanca`

---

## 3. Pull Requests (PRs)

Ao abrir um PR, certifique-se de:
1. Utilizar o **GitHub CLI** (`gh pr create`) ou a interface web.
2. Preencher o checklist que aparecerá automaticamente no corpo do PR.
3. Aguardar a revisão do mantenedor.

---

## 4. Publicação de Pacotes

A publicação oficial no **GitHub Packages** é realizada **apenas após o merge na `main`** e exclusivamente através do script de automação:
* `./scripts/publish.sh NomeDoProjeto`

> **Nota:** Apenas colaboradores autorizados possuem o Token (PAT) necessário para a publicação final.
