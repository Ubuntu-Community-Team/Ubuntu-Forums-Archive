---
title: "Problem with package modemmanager"
date: 2012-12-22
forum: Installation &amp; Upgrades
---

### Post by cesarrodrigues on 2012-12-22
Hi everybody,

I have recently installed Ubuntu 12.10 amd64 and everything was going OK. Since I have made an "apt-get upgrade", I am seeing the messages below when I try to install any package:

"Você deve querer executar 'apt-get -f install' para corrigí-los:
Os pacotes a seguir têm dependências desencontradas:
 modemmanager : Depende: libgudev-1.0-0 (= = 147) mas 1:175-0ubuntu13 está para ser instalado
E: Dependências desencontradas. Tente 'apt-get -f install' sem nenhum pacote (ou especifique uma solução)."

My question: how can I disable the package "modemanager"? How can I solve this problem?

I've deleted the contents of the directory "/var/cache/apt/archives" but this didn't solve the problem.

---

### Post by fantab on 2012-12-23
Please post the errors in ENGLISH. Use Google Translate if you have to.

To uninstall:

$ sudo apt-get --purge modemnanager

---

