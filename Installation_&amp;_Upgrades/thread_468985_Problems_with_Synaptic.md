---
title: "Problems with Synaptic"
date: 2007-06-09
forum: Installation &amp; Upgrades
---

### Post by brunohungaro on 2007-06-09
W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release: Erro desconhecido executando gpgv
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release: Erro desconhecido executando gpgv
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release: Erro desconhecido executando gpgv
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release: Erro desconhecido executando gpgv
W: GPG error: [ftp://sft.if.usp.br](ftp://sft.if.usp.br) feisty Release: Erro desconhecido executando gpgv
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release: Erro desconhecido executando gpgv
W: GPG error: [ftp://sft.if.usp.br](ftp://sft.if.usp.br) feisty-updates Release: Erro desconhecido executando gpgv
W: GPG error: [ftp://sft.if.usp.br](ftp://sft.if.usp.br) feisty-security Release: Erro desconhecido executando gpgv
W: GPG error: [ftp://sft.if.usp.br](ftp://sft.if.usp.br) feisty-backports Release: Erro desconhecido executando gpgv
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release: Erro desconhecido executando gpgv

i dont find any solution!

:(

anyone can help-me?

---

### Post by zvacet on 2007-06-09
```
sudo aptitude update && sudo aptitude upgrade
```

If that doesn´t help 

```
cat /etc/apt/sources.list
```

and post it here

---

