---
title: "Samba package causes Dapper update to abort"
date: 2006-06-06
forum: Installation &amp; Upgrades
---

### Post by jchau on 2006-06-06
When the update from Ubuntu 5.10 to Ubuntu 6.06 LTS (using the GUI update manager) was installing the Samba package, I got this error:
```
installArchives() failed
```
and it returned an error.  The update then continued to what appeared to be the end of the "Downloading and Installing" step and then aborted.  This left the "Cleanup" and "Reboot" steps incomplete.

I have tried to reinstall the Samba package, but it gives me the same error each time.  

How do I fix this?
Is my Dapper upgrade complete? How do I complete it?

Thank you!

---

### Post by cyberideias on 2006-06-06
hello all

my update was perfect, except about the SAMBA.

I think the Swat and Cups maybe dont work too…    

I trieded installation, upgrade, reinstallation and purge for SAMBA and always it gives some error

I decided to erase and reinstall everything. 

And... not purge!    

See the error below: 

```
regis@chiquinha:~$ sudo apt-get --purge remove samba
Lendo Lista de Pacotes... Pronto
Construindo Árvore de Dependências... Pronto
Os pacotes a seguir serão REMOVIDOS:
  samba* swat*
0 pacotes atualizados, 0 pacotes novos instalados, 2 a serem removidos e 2 não atualizados.
É preciso fazer o download de 0B de arquivos.
Depois de desempacotar, 9269kB de espaço em disco serão liberados.
Quer continuar [S/n] ? s
(Lendo banco de dados ... 158223 arquivos e diretórios atualmente instalados.)
Removendo swat ...
Apagando arquivos de configuração de swat ...
Removendo samba ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: erro processando samba (--purge):
 subprocesso pre-removal script retornou código de saída de error 102
Erros foram encontrados durante processamento de:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1) 
```

---

### Post by jchau on 2006-06-06
Does anyone else have this problem? anyone have a fix?

---

### Post by :::mL::: on 2006-06-06
hi jchau!

i had the same problem - but installation (upgrade) was finish.


try next (i found that on [https://launchpad.net/distros/ubuntu/+source/samba/+bug/48705]("https://launchpad.net/distros/ubuntu/+source/samba/+bug/48705"))


first delete files:

sudo rm /etc/rc3.d/K09samba

sudo rm /etc/rc2.d/K09samba

and than:

sudo apt-get remove samba

and new installation:

sudo apt-get install samba


it worked for me!  :D

---

### Post by jchau on 2006-06-06
Thanks. It worked. 

Now to finish the Dapper upgrade.  Anyone know how to do that? Update manager no longer shows the "Upgrade" button.

---

### Post by sambram on 2006-06-07
Does anyone have a solution to finishing the upgrade? I think I'm stuck in the same place as jchau. 

Apt-get -f install/remove both yield nothing. Two packages are being held back, and there are zero to be installed or removed.

---

### Post by :::mL::: on 2006-06-09
maybe:

sudo apt-get dist-upgrade !?

---

### Post by Garyu on 2006-06-09
Humm... I had this error too... "samba - underprocess post-installation script gav felkod 102"... So I rebooted "windows-style" and it seemed to boot me into dapper. Although, samba always gave the above error whenever I tried to start Synaptic or do any changes. However, the above tip about running "sudo apt-get dist-upgrade" worked like a charm!

First 13 packages were downloaded. Then installed. And voila; everything works fine, and samba stopped complaining. =)

Yay! :) Thanks a lot. :cool:

---

### Post by jchau on 2006-06-11
I'm still wondering though. Since the upgrade aborted before it finished. What steps are we missing? Is there a list of the steps somewhere? Is there an automatic or manual way of finishing the install or is it finished?

---

