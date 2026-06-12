---
title: "[SOLVED] Antivirus"
date: 2007-12-13
forum: Installation &amp; Upgrades
---

### Post by LinuxIsInnovation on 2007-12-13
Which antivirus and firewall do I use for Gutsy 7.10 x64?

---

### Post by LinuxIsInnovation on 2007-12-13
Please provide the link for that...

---

### Post by Partyboi2 on 2007-12-13
ubuntu doesn't actually need a anti virus program, as it is very rare for linux to get virus. But if you are wanting to install a anti virus program 
You have
Clamav 
[http://www.clamav.net/](http://www.clamav.net/)

---

### Post by PmDematagoda on 2007-12-13
An antivirus for Linux would just be a waste of resources since there are virtually no viruses for it, though an antivirus guard may be used when you exchange files between Windows PCs often such as through E-mail or through the network. But again, an AV guard for Linux is mostly only for the protection of Windows machines, not for Linux ones.

---

### Post by OrangeCrate on 2007-12-13
> **sayakb said:**
> Which antivirus and firewall do I use for Gutsy 7.10 x64?

These will help you to understand security on Linux. It's not the same as with Windows.

[http://psychocats.net/ubuntu/security](http://psychocats.net/ubuntu/security)

[http://www.linuxclues.com/articles/21.htm](http://www.linuxclues.com/articles/21.htm)

---

### Post by atlfalcons866 on 2007-12-13
The virus needs root access to write to the / area so it is very rare for the virus to get on the hard drive. Viruses are a windoze thing.

---

### Post by JangMunho on 2007-12-13
Antivirus, yes, you can install them, but they're not for linux virus, they are for Windows virus. You can kill the virus in your flash disk. It's safe because linux won't get affected.
There is a list, maybe not complete:
Antivir (free of charge)
Avast! (free of charge)
AVG Workstation for Unix (free of charge)
BitDefender (free of charge)

And firewall, just try:
sudo apt-get install firestarter

---

### Post by DrMega on 2007-12-13
> **atlfalcons866 said:**
> The virus needs root access to write to the / area so it is very rare for the virus to get on the hard drive. Viruses are a windoze thing.

Careful here. Viruses predate Windows. Linux is certainly far more secure than Windows, but we should not take it for granted that we don't need to protect our machines. I don't but I'm a bit complacent, and I don't mind do a full reinstall if necessary, but if I couldn't be bothered to do a reinstall from time to time, I would be looking to put an antivirus program on just in case.

---

### Post by daengbo on 2007-12-13
Check my page on this:
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)

---

### Post by LinuxIsInnovation on 2007-12-14
> **atlfalcons866 said:**
> The virus needs root access to write to the / area so it is very rare for the virus to get on the hard drive. Viruses are a windoze thing.

Isn't this like UAC in Vista? Sorry, elucidating: UAC is a copy of this :D

---

### Post by LinuxIsInnovation on 2007-12-14
Well, Ive installed Avast on my Linux and tried (now uninstalled) ClamAV.. But actually I wanted something with an on-access protection... The main reason being that we people use file sharing (thru applications like IP Messenger) in our college and all other students in the hostel have Windows installed.. Most of them suffer from virus problems. So please tell me which AV has on access protection..

---

### Post by PmDematagoda on 2007-12-14
In a way it is, but it is not as efficient as the system that is currently used in Linux and which has been used in Linux from about the time it was first conceived. Windows used to follow a system where every user was given full permissions, but this is really ineffective, so basically Vista is trying to copy Linux now;).

---

### Post by LinuxIsInnovation on 2007-12-14
> **PmDematagoda said:**
> In a way it is, but it is not as efficient as the system that is currently used in Linux and which has been used in Linux from about the time it was first conceived. Windows used to follow a system where every user was given full permissions, but this is really ineffective, so basically Vista is trying to copy Linux now;).

Yeah.. just the same way it has copied Leopard.. ;)

---

### Post by LinuxIsInnovation on 2007-12-14
Sorry for posting it here but most of my doubts about Ubuntu have remained un-answered
PS: Im a total newbie in Linux and as expected, Ive got loads of problems :D
I need some time to accept this Windows to Linux changeover :)

Anyway, please do reply here to whenever you people get some time.. Thank you
[http://ubuntuforums.org/showthread.php?p=3949319#post3949319](http://ubuntuforums.org/showthread.php?p=3949319#post3949319)

---

### Post by LinuxIsInnovation on 2007-12-14
@PmDematagoda + Everyone else
So which AV should I go with.. please consider On-access protection also..

---

### Post by mikewhatever on 2007-12-14
As far as I know, no AV for linux used on access protection. You do not need an AV, let along on access. Windows viruses your friends are worried about can't harm you because you do not use Windows.
For more info on security, look here -->[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by LinuxIsInnovation on 2007-12-14
Ok.. seems like I will stick to avast then... 
Thanks for your advice every one.. :)
Have a good day.. :D

---

### Post by LinuxIsInnovation on 2007-12-16
Avast antivirus takes a hell lot of time to upgrade its database.. My bandwidth is 2mbps, still, it takes about 5-7 minutes.. :(

---

### Post by OrangeCrate on 2007-12-16
> **sayakb said:**
> Avast antivirus takes a hell lot of time to upgrade its database.. My bandwidth is 2mbps, still, it takes about 5-7 minutes.. :(

If you had read the two links I provided to you in post #5, you wouldn't be wasting your time trying to install an antivirus program. You don't need one.

---

### Post by mikewhatever on 2007-12-16
> **sayakb said:**
> Avast antivirus takes a hell lot of time to upgrade its database.. My bandwidth is 2mbps, still, it takes about 5-7 minutes.. :(

We can't help you with that. Try Avast forums instead.

---

### Post by LinuxIsInnovation on 2007-12-16
I need an antivirus for my Windows files' protection.. I dont want to send/receive infected files.. These infected files will affect my system or not, is secondary..

---

### Post by OrangeCrate on 2007-12-16
Post deleted, any additional advice from me would be redundant.

---

### Post by LinuxIsInnovation on 2007-12-17
OK.. thanx for the info

---

