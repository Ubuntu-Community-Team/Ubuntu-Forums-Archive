---
title: "Tried to upgrade from 10.04 to 10.10b1, now I can't boot. Help!"
date: 2010-09-09
forum: Installation &amp; Upgrades
---

### Post by DemanRisu on 2010-09-09
Title says it all, I guess.

The story:
I started out with UNR 10.04. After getting entirely sick of the interface, I deleted the gconf, etc., folders which held all the system settings. This gave me the normal Ubuntu interface. Fast forward a month, and my Ubuntu has heaps of tools for security testing (such as Wireshark, Nmap, Metasploit, etc.). I then, this morning, attempted to upgrade via synaptic to the first beta of Maverick Meerkat. I got a few errors during the upgrade process, related to installing programs. Thinking this was to be expected, I clicked "ok" on everything. 
Two hours later, the installation failed.
I hit "rollback" (or whatever the option was), and waited. After a reboot, I expected to see my lovely purple screen, but instead I saw a prompt saying "grub rescue>".
I'm writing this on a 10.04 Live USB.

How can I fix my Ubuntu and, if possible, keep my files? (I can access all the filesystems on my HDD)

This machine is an Eee PC 904HA.

Thanks in advance for help. :)

P.S.: I know my way around Linux - I can utilize simple commands and find my way around a filesystem in bash and compile things.

---

### Post by mörgæs on 2010-09-09
Welcome to the forum.

It is good that you test the new version, but in general the help should go from the users to the developers for a version in beta, not the other way around. 

Still, this forum might help you:

[http://ubuntuforums.org/forumdisplay.php?f=385](http://ubuntuforums.org/forumdisplay.php?f=385)

---

### Post by DemanRisu on 2010-09-09
This doesn't help me at all. This is still a 10.04 problem, because it was *supposed* to roll back after the failed upgrade... but it evidently didn't.

---

### Post by DemanRisu on 2010-09-09
-bump-

-oh, and it gives me a "kernel not found" error, if that helps. Can I recover from that?

---

### Post by tyblogger5 on 2010-09-09
I haven't used the beta, but try to rescue the grub loader:

[https://help.ubuntu.com/community/Grub2#Reinstalling from LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling from LiveCD)

Hope this helps!
Tariq

---

### Post by howefield on 2010-09-09
> **DemanRisu said:**
> This doesn't help me at all. This is still a 10.04 problem, because it was *supposed* to roll back after the failed upgrade... but it evidently didn't.

10.04 knows nothing about rolling back, it is a 10.10 issue.

---

### Post by DemanRisu on 2010-09-09
> **tyblogger5 said:**
> I haven't used the beta, but try to rescue the grub loader:

[https://help.ubuntu.com/community/Grub2#Reinstalling from LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

Hope this helps!
Tariq

It didn't. :( Thanks for the suggestion anyway.

Now, I think the focus of my question is salvaging my files...

(just a little thing that made me laugh here, I couldn't access my /usr partition and started to freak out, then I realized that with sudo nautilus, I could. Ubuntu gives you the coolest things when you ask it in a stern voice.)

If I wipe my current install (that being the partition which everything EXCEPT /usr was on), can I still use (and keep the files from) my previous /usr partition? I've checked, and the files are still there (thank goodness!).

I really appreciate all your help :D

---

### Post by tyblogger5 on 2010-09-09
No problem, just wish I could help more

---

