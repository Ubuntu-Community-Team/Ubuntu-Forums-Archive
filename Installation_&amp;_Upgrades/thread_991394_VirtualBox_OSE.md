---
title: "VirtualBox OSE"
date: 2008-11-23
forum: Installation &amp; Upgrades
---

### Post by spawn. on 2008-11-23
I am dual booting XP Professional and Ubuntu 8.04. I installed VirtualBox OSE on Ubuntu because I was bored. I decided to run VirtualBox OSE, open MS Word, and save a small file. Then I logged out of Ubuntu to boot into XP Professional to locate the file I saved. I wasn't surprised nor upset that I could not locate the file that I saved when using the VirtualBox.

My question is: Is this the expected outcome? 

or

Was I supposed to find the file on the original?

---

### Post by Partyboi2 on 2008-11-24
You could try setting up file sharing following [[COLOR=Blue]this[/COLOR]]("https://help.ubuntu.com/community/VirtualBox#Sharing%20Folders%20Between%20Host%20and%20Guest") guide. But this will only allow you to share between the guest os and the host.

---

### Post by Rplus9 on 2008-11-24
normally the virtual machine is contained in a "hard-drive" file somewhere on your linux partition.

it sounds like you're dual booting, so when you hop over to your windows partition, then yes it won't be there.

did you duplicate your windows partition in virtualbox?  I haven't tried doing that (no windows partition left to dupe) but, if you did the two are now separated, sort of like clones.

What you can do is set up Wine to run programs off your windows partition.  I did that to play world of warcraft before I re-partitioned the windows side.  Then what you do in Wine to the windows partition will exist when you boot windows.

---

### Post by spawn. on 2008-11-24
So before I took any drastic measures, I opened up my Windows partition in Linux (as it shows it being a mounted volume). I clicked on My Documents and Settings, was prompted to enter my root password, then I was able to copy and paste a file that I made in Linux onto my Windows partition. The only problem now is that I have to log off Ubuntu and boot Windows up to actually get what I want done on it. (Technically, I could do the job on Linux but I paid like $300 bucks for that M$ software last year and I want to get my money's worth of it.)

I wanted to try duplicating the partition using VirtualBox, the only issue is that my ram is usually being raped by all the applications I run or have as running services on both operating systems.

---

