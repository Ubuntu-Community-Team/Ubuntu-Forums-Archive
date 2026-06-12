---
title: "Apt stopped working"
date: 2007-02-03
forum: Installation &amp; Upgrades
---

### Post by ufa on 2007-02-03
Hello all
I dont know what happened, but my apt is working for installing/removing software anymore.

Everytime i try to install something, it returns to me:

sudo apt-get install wesnoth

Lendo Lista de Pacotes... Pronto
Construindo Árvore de Dependências       
Reading state information... Pronto 
É preciso fazer o download de 0B/69,8MB de arquivos.
Depois de desempacotamento, 109MB adicionais de espaço em disco serão usados.
Quer continuar [S/n] ? 
Selecionando pacote previamente não selecionado libsdl-net1.2.
(Lendo banco de dados ... dpkg: erro processando /var/cache/apt/archives/libsdl-net1.2_1.2.5-7_i386.deb (--unpack):
 falha em buffer_read(fd): lista de arquivos do pacote `openoffice.org-evolution': Argumento inválido
E: Sub-process /usr/bin/dpkg received a segmentation fault.

It is in portuguese, so i will translate:

(reading database.... dpkg: error processing /var/cache/apt/archives/libsdl-net1.2_1.2.5-7_i386.deb (--unpack): 
Failed in buffer_read(fd): packet list archive 'openoffice.org-evolution': Invalid Argument


So i cant do anything, i tried to purge/remove the ooo-evolution, and nothing works, always i fell in the same error. 
I tried:

 dpkg --configure -a
apttitude install openoffice.org-evolution

With the same error. I tried to "fsck /dev/hda1 -r" but returns clean.

Does someone have a clue?

Ufa

---

### Post by raul_ on 2007-02-03
Olá. Podes postar o teu ficheiro sources.list?

Translation:

Hello. Can you post your sources.list file?

My guess is that you have a broken repository or something. Try running

```

sudo dpkg -configure -a
sudo apt-get autoclean
sudo apt-get update

```

---

### Post by ufa on 2007-02-03
I think is not a sources.list problem, because the apt-get update command runs without a problem.
The problem appears only when i try to install/remove something.
anyway, here is my sources.list:

I ran the commands that you asked me, without problem.
```
cat /etc/apt/sources.list
# 
# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted


#deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

deb http://br.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://br.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://br.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://br.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://br.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://br.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse


#deb http://security.ubuntu.com/ubuntu edgy-security main restricted
#deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe


######################## Novos

#deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse

#deb http://archive.ubuntu.com/ubuntu edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
#deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
#deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
#deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse














#AUTOMATIX REPOS START

deb http://wine.lowvoice.nl/apt edgy main

deb http://www.getautomatix.com/apt edgy main

deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy universe multiverse
#AUTOMATIX REPOS END

deb http://ubuntu.beryl-project.org edgy main

```

---

### Post by raul_ on 2007-02-03
Just for testing purposes, could you backup that file (rename it to sources.list.old) and create a new one like in this page:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories")

Do an update and try again.

---

### Post by ufa on 2007-02-03
OK, I will do it, and post results here soon

---

### Post by ufa on 2007-02-04
```
ufa@ubuntu-lulu:/etc/apt$ sudo cp sources.list sources.list.bk.ufa
Password:
ufa@ubuntu-lulu:/etc/apt$ rm sources.list
rm: remover arquivo comum `sources.list' protegido contra escrita? 
ufa@ubuntu-lulu:/etc/apt$ sudo rm sources.list
ufa@ubuntu-lulu:/etc/apt$ sudo vi sources.list
ufa@ubuntu-lulu:wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
sudo apt-get update
OK
ufa@ubuntu-lulu:/etc/apt$ sudo apt-get update
...

sudo apt-get install wesnoth wesnoth-data wesnoth-editor wesnoth-ei wesnoth-httt wesnoth-music wesnoth-server wesnoth-trow wesnoth-tsg wesnoth-ttb wesnoth-utbs
...
Selecionando pacote previamente não selecionado libsdl-net1.2.
(Lendo banco de dados ... dpkg: erro processando /var/cache/apt/archives/libsdl-net1.2_1.2.5-7_i386.deb (--unpack):
 falha em buffer_read(fd): lista de arquivos do pacote `openoffice.org-evolution': Argumento inválido
E: Sub-process /usr/bin/dpkg received a segmentation fault.

```

Same thihg :(

---

### Post by deadlydeathcone on 2007-02-04
> **ufa said:**
> ```

Selecionando pacote previamente não selecionado libsdl-net1.2.
(Lendo banco de dados ... dpkg: erro processando /var/cache/apt/archives/libsdl-net1.2_1.2.5-7_i386.deb (--unpack):
 falha em buffer_read(fd): lista de arquivos do pacote `openoffice.org-evolution': Argumento inválido
E: Sub-process /usr/bin/dpkg received a segmentation fault.

```

Same thihg :(

Ufa, I've had this exact error happen twice, and both times it was the fault of a corrupt filesystem on my root partition. Generally, if you mess around too much with dpkg at this point you run the risk of completely borking things up beyond repair.

The trick that always cleared things up for me was ```
sudo touch /forcefsck
``` which forces an automated check upon reboot, that subsequently fails and drops to a maintenance shell that allows you to run fsck manually. When this happens don't follow fsck with any other commands such as -r or -a or it won't succeed. Once it's done you'll be able to use apt again, but you'll probably have to reinstall a few packages to get things back to normal.

I hope that works (it did for me five minutes ago). If it doesn't you may be in trouble.

---

### Post by ufa on 2007-02-07
Hello deadlydeathcone
I will try that in the weekend, and post the results
thank you fot the atention. I was begining to suspect from the filesystem, but i ran fsck and it was clean :(

well, weekend we will have a answer...
see ya
Ufa

---

### Post by ufa on 2007-02-11
It worked. I did a fsck and it corrected some inodes, and, violá....
everything is fine!!
Thanks a bunch!!!

---

### Post by Sulamita on 2007-09-25
I also have this problem. I ran fsck, lots of errors. But now I have this error:

(Reading database ... 
dpkg: serious warning: files list file for package `myspell-pt' missing, assuming package has no files currently installed.
dpkg: error processing /var/cache/apt/archives/app-install-data-commercial_7.3_all.deb (--unpack):
 unable to open files list file for package `vino': No such device or address
Errors were encountered while processing:
 /var/cache/apt/archives/app-install-data-commercial_7.3_all.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

How can I fix it?

---

### Post by ufa on 2007-09-26
In my case, it was corrupted filesystem. Try to fsck it in the unmounted device!

---

### Post by Sulamita on 2007-09-30
> **Sulamita said:**
> I also have this problem. I ran fsck, lots of errors. But now I have this error:
....


Like I said, I already did it and no solution. any other idea?

Also, can someone tell me why filesystem errors made the package management system stop working?

---

### Post by ufa on 2007-09-30
maybe because it corrupted the files signatures?
When you ran fsck, did it correct those erros?
Try to run it again now, and see if new errors are shown. It yes, I think you HD is going to hell :D

---

### Post by Pumalite on 2007-09-30
Try:

sudo dpkg --remove --force-remove-reinstreq <packagename>

---

### Post by Sulamita on 2007-09-30
A corrupted file signature should cause problems to that package, not the entire package managment system.
And again, I did ran the fsck, several times. You could try to have new ideas or if you don't, repeating over and over and over the same one will not fix the problem.

Anyway, I fixed it.

I downloaded vino_2.18.1-0ubuntu1_i386.deb, extracted the list of files with dpkg --contents, put the output in a file and replaced broken /var/lib/dpkg/info/vino.list file.

If anyone could explain why one broken file crashes the entire package management system, I would be glad to know. This error prevent me to install, upgrade or remove any package, from kernel-headers to scroobler.

---

### Post by ufa on 2007-09-30
Thank you for your tip. Very polite indeed :/

---

