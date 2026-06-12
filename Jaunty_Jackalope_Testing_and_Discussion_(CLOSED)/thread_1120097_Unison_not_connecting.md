---
title: "Unison not connecting"
date: 2009-04-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by itsjustarumour on 2009-04-08
Hi all,

Having some trouble with Unison.  

I've been using it for the last few months to synchronise various folders between my PC and laptop, both running Intrepid.  Since updating the laptop to Jaunty, when I run Unison on the PC, select a profile and try and connect I just get the message:

> **Fatal error** Lost connection with server

I've checked the obvious things:

- all the relevant packages are installed, on the correct machine
- both machines are using the same version of Unison 2.25.57 (I understand Unison can be a bit fussy if these don't match)
- the IP addresses are both correct (192.168.1.2 and 192.168.1.3 in this case)
- the network connections are OK (I can ping each machine from the other one)

Anybody got any ideas on how I can troubleshoot this?  Could it be a port issue?

Best Regards,

itsjustarumour

---

### Post by itsjustarumour on 2009-04-09
Bump.  Anyone?

---

### Post by itsjustarumour on 2009-04-11
Bump.

---

### Post by itsjustarumour on 2009-04-13
Bump.  Has anyone got Unison working in Jaunty, or synching between an Intrepid and a Jaunty machine?

---

### Post by jlacroix on 2009-04-13
I use Unison to sync between a Jaunty laptop, a Jaunty desktop, and a portable hard drive. It works for me.

The only thing I can think of (and I'm sure you tried these things already, but it's all I have and know):

Reboot both machines

or

One of them doesn't have the openssh server installed, or it got removed in the upgrade process.

---

### Post by itsjustarumour on 2009-04-13
> **jlacroix said:**
> I use Unison to sync between a Jaunty laptop, a Jaunty desktop, and a portable hard drive. It works for me.

The only thing I can think of (and I'm sure you tried these things already, but it's all I have and know):

Reboot both machines

or

One of them doesn't have the openssh server installed, or it got removed in the upgrade process.

Hi, thanks for the post jlacroix but I've already checked/tried that.  I'm starting to wonder if this might actually be an issue with GNOME Keyring or Seahorse or something...

---

### Post by jlacroix on 2009-04-13
> **itsjustarumour said:**
> Hi, thanks for the post jlacroix but I've already checked/tried that.  I'm starting to wonder if this might actually be an issue with GNOME Keyring or Seahorse or something...

It shouldn't be, because Unison (at least with me) uses the keyrings.

I had this problem too and it was because one of the following packages was missing on one of the machines:

openssh-server (I think that's what it's called), unison, and unison-gtk. I am not sure if each of the three are required but I just went ahead and installed them all on each machine.

If that's not the case, I can only guess that it's a version conflict between what ships with Jaunty and what ships with Intrepid. Although it may break things, you could try installing Jaunty's version of the packages on each machine. Other than upgrading to Jaunty I'm not sure what else to try.

Did you try disabling Gnome's keyring?

---

### Post by tgoose on 2009-04-13
I'm successfully syncing between an Intrepid and Jaunty computer.  They both have version 2.27.57-1ubuntu1 installed.  I can't remember if I had to fix this to get it to work to start with or not, I'm afraid.  But definitely it is doable.

---

