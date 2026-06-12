---
title: "Opera dont want to install"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by profediego on 2007-04-20
Hi guys, hope everyone is doing OK??

I am using ubuntu 6.10, 2 days ago, the automatic updates tell me there are updates, so i try to install them.  everything goes well except for one update regarding Opera web Borwser, it doesnt make the update thats what the automatic updates app told, since then opera stops working, so i make  a "sudo apt-get remove opera" and the try to install it again... but it just keep me sayin there are dependancies problems:

Los siguientes paquetes tienen dependencias incumplidas:
  opera: Depende: libc6 (>= 2.5-0ubuntu1) pero 2.4-1ubuntu12.3 va a ser instalado
         Depende: libgcc1 (>= 1:4.1.2) pero 1:4.1.1-13ubuntu5 va a ser instalado
         Depende: libqt3-mt (>= 3:3.3.8really3.3.7) pero 3:3.3.6-3ubuntu3.1 va a ser instalado
         Depende: libstdc++6 (>= 4.1.2) pero 4.1.1-13ubuntu5 va a ser instalado
E: Paquetes rotos

The thing is i dont know how to fix dependancy problem thing, cause i hace try to update the libraries above but it seems to be that those are the newest inubuntu repos, so i dont know how to proceed could somebody out here please tell me what i can do?

---

### Post by shirsch on 2007-04-20
Yes, something is definitely broken in the edgy repository.  That package seems to want levels of libc6 that are actually distributed in Feisty.  Dozens of folks are tripping over this.

Hopefully, one of the repository admins will straighten it out soon.

---

### Post by profediego on 2007-04-21
i hope so too, meanwhile i guess i will have to wait.. :(

---

### Post by graeme_p on 2007-04-24
I still have the same problem.

I started a thread asking how to report bugs in the Canonical  Commercial repo, and got no replies.

The problem seems to be incorrect dependencies, so it ought to be quickly fixable, when they notice it.

---

### Post by HeyItsMatt on 2007-04-24
I don't know exactly if this is related to the problem you guys are having, but I tried to load up Opera this morning and it did not want to load, it kept giving me a crash error.  I uninstalled it using Synaptic and then went to reinstall it, but suddenly cannot find any "opera" packages in Synaptic despite using the "reload" button, and updating / upgrading it from command line.  I can't find an opera package using "sudo aptitude install" either.

---

### Post by graeme_p on 2007-04-24
It crashes here too. The crash is probably still the same problem. If you have the Dapper version of Opera, it is apparently not compatible with Edgy. It is not getting upgraded because the package is broken, so it crashes.

---

### Post by profediego on 2007-04-24
Still havin the same problem, PLEASE SOMEONE AT CANONICAL FIX THIS... I need to use opera... :(

---

### Post by chek2fire on 2007-04-25
i still have this problem.opera remain break :guitar:

---

### Post by graeme_p on 2007-04-28
I think the message is clear:

Do not rely on the Canonical repositories (except possibly for LTS releases). I am going to download Opera from their website and install it from there.

I assume that because the Canonical repo has never really taken off for whatever reason, that they are  not prepared to put in any effort into supporting it.

---

