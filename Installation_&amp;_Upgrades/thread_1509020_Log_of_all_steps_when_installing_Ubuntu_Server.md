---
title: "Log of all steps when installing Ubuntu Server?"
date: 2010-06-13
forum: Installation &amp; Upgrades
---

### Post by tnek on 2010-06-13
Hi,

I'm about to install Ubuntu Server 10.04 on my home server. I have looked around, a lot, without finding a nice way to record or log all the steps of the installation.

I see two general paths of how my problem might be solved:

[LIST]
[*]Is there any installation log file which I could look in to see which options I choose? It would be best if it included all steps, including partitioning and, in my case, setting up an encrypted volume with a KVM-volume inside it.
[*]Are there any ways to record the installation or take screenshots of it? It's done using the console (with no X window system available). Maybe fbgrab could work, but I do not know how to make it available during the installation.
[/LIST]
I could also use a pen and paper. But that is error prone as I do not have the patience to write *everything* down. It's my last resort though.

All ideas appreciated!

---

### Post by oldfred on 2010-06-14
If it is server are you doing everything from the command line?

I installed Karmic (desktop) as a clean install and realized I wanted the same install to my laptop and very similar when Lucid came out. So I tried to do as much as possible with command line, listed history ( history ) and converted most of it to a bash file that I could rerun all the commands.

---

### Post by tnek on 2010-06-19
I'm doing it using the command line installer. The text menu driven interface. So, I don't know how to convert that into a script. Is it possible?

---

### Post by oldfred on 2010-06-19
I saved all the things I did after the actual install to customize my system.

I have not done  a server install but some places to start looking:
[https://help.ubuntu.com/10.04/serverguide/C/automatic-updates.html](https://help.ubuntu.com/10.04/serverguide/C/automatic-updates.html)
[http://searchsystemschannel.techtarget.com/generic/0,295582,sid99_gci1377934,00.html](http://searchsystemschannel.techtarget.com/generic/0,295582,sid99_gci1377934,00.html)
[https://help.ubuntu.com/community/KickstartCompatibility](https://help.ubuntu.com/community/KickstartCompatibility)

---

