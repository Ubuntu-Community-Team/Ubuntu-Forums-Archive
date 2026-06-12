---
title: "I want to re-install 386 feisty over a 64amd feisty"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by mpooley on 2007-04-27
But i dont want to go through all the problems setting up my preferences etc.
I have a seperate Home Partition and i want to back up all the settings to a backup on there.

My problem is i dont know what files/folders i should backup
can anyone tell me please

---

### Post by lw5 on 2007-04-27
Well, if you have a seperate home partition, there is nothing to wory about. Just re-install feisty on its own partition and mount your home partition to /home..

I did the same thing last week. All settings were intact.

---

### Post by mpooley on 2007-04-27
> **lw5 said:**
> Well, if you have a seperate home partition, there is nothing to wory about. Just re-install feisty on its own partition and mount your home partition to /home..

I did the same thing last week. All settings were intact.

ooh thanks !!

---

### Post by modorf on 2007-04-27
might want to save your /etc folder too.

---

### Post by mpooley on 2007-04-28
> **modorf said:**
> might want to save your /etc folder too.

Ok one more question!
I've installed the i386 feisty over the amd64bit and i seem to ave kept all my user preferences mail etc which is great :) 
but it looks like i will have to re-install all my programs like Opera etc.

is this why i backed up etc?  what will happen if i restore etc?  i dont want to do anything i dont understand? :confused:

---

### Post by fwojciec on 2007-04-28
Don't restore /etc folder (it holds configuration files for your system) - at least I wouldn't - I would expect things to break when you restore /etc folder from 64 bit system on a 32 bit system.

The programs you installed on 64 bit system were 64 bit versions, you'll have to reinstall all programs, because you need 32 bit versions for your 32 bit system.

---

### Post by mpooley on 2007-04-28
> **fwojciec said:**
> Don't restore /etc folder (it holds configuration files for your system) - at least I wouldn't - I would expect things to break when you restore /etc folder from 64 bit system on a 32 bit system.

The programs you installed on 64 bit system were 64 bit versions, you'll have to reinstall all programs, because you need 32 bit versions for your 32 bit system.

Thanks I did suspect this might be the case!

Can you confirm that in future if i re-install an i386 on an i386 system that restoring /etc would re-instate all  my programs???

thanks

---

### Post by fwojciec on 2007-04-28
The files in the /etc directory are only the configuration files for system and (some) programs (most configuration files for programs you generally use are actually stored in your home folder anyways, /etc has configurations for your devices, start up scripts, hardware, network configuration and so on), so they would not restore your programs.  They could however mess up configurations of programs which are already installed.

You can safely look inside the /etc directory and see what's there - most of these files are actually editable and can be used to manually configure your system if you want to use a more hands-on approach.  Be careful about editing those files though, because it is easy to mess things up if you don't know what you're doing ;)

The actual programs are installed into multiple directories so there is no easy way to backup all your installed programs - it is much easier to reinstall them.

---

### Post by mpooley on 2007-04-28
Thankyou!  :)  Most helpfull

---

### Post by fwojciec on 2007-04-28
You're welcome :)

---

