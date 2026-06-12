---
title: "Install/Upgrade to Ubuntu 11.04 on a Toshiba Satellite = MANY PROBLEMS!"
date: 2011-05-20
forum: Installation &amp; Upgrades
---

### Post by Brushstroke on 2011-05-20
Hello everyone. 

Awhile back when Ubuntu 11.04 came out, I tried upgrading from my then 10.10 install on my Toshiba Satellite L455D laptop. The upgrade went smoothly. After I rebooted, I went into the Unity desktop and pretty much immediately hated it. But I was still pleased with being able to fallback to a Gnome 2 desktop in the login options. I then shut the laptop off and went out with a few friends. I came back that night and turned it back on expecting to be greeted with a login screen, but that didn't happen. I was greeted with a lovely black screen. I kept rebooting and got the same result. So, to get at least a stable system that I could work with I resorted to reinstalling Ubuntu 10.04 LTS. 

I then got the idea that maybe I should try installing 11.04 from a CD rather than upgrading. I've learned that it's better, as a rule, to install from scratch rather than upgrade. I tried running the Live CD to test it out before installing but it wouldn't even boot into the live environment. I tried two other CDs thinking it might have been a bad burn and got the same result. Frustrated and thinking, "Eh, it'll work fine when I get it installed," I just installed anyway without testing. This time, I had the same problem as I did when I upgraded. It wouldn't boot. It just took me to a black screen. 

So, I just scrapped 11.04 (again) and now I'm running 10.04 LTS with a few PPAs to get the latest versions of a few programs. I've been considering going back to 11.04, scrapping Unity and installing Gnome 3 in its place. I've read that it's worked quite well for some people. 

So, I guess I have three questions.

[LIST]
[*]Has anyone used Ubuntu 11.04 on a Toshiba Satellite (or similar) laptop with any luck? I have a feeling the black screen problem is related to my ATI Radeon card in here (the manufacturer website says it's an ATI Radeon 3100).
[/LIST]

[LIST]
[*]Is there a problem with the 64-bit .ISO for 11.04 or something? I tried the 32-bit .ISO and it worked and booted into the live environment without any problems at all.
[/LIST]

[LIST]
[*]Has anyone had any luck installing Gnome 3 in Ubuntu 11.04, and are there any problems I should watch out for if I decide to do it (provided I'm even able to get 11.04 running)?
[/LIST]
Any input is greatly appreciated. Thank you!

---

### Post by Hedgehog1 on 2011-05-20
Greetings!

The second sticky on this forum is about this very issue and it's resolution:  [http://ubuntuforums.org/showthread.php?t=1743535]("http://ubuntuforums.org/showthread.php?t=1743535")

That is your best place to start.

***The Hedge***

:KS

---

### Post by syl-via on 2011-07-29
Yes, I run into the same problem too. The problem is related with the drivers for ATI Radeon card, which since always brings much more problems than it should. 

After like 1h of trying to make it work, getting to a point like.. 'OK Ubuntu 11.04 it's you last chance' ... I found somewhere this procedure:

1. Start the GRUB menu (usually it loads automatically, if not than press few times SHIFT on boot and it should show up) 

2. Edit (press e) the first boot option (not the recovery mode) 

3. In the line with 'linux /boot/...... ' removing everything that goes after 'ro' namely 'quiet splash vt.handoff=7' and replace it with 'nomodeset'

4. CTRL+x will start the system with the new option.

5. When finally you start the system go to System->Hardware->Additional Drivers

6. Restart

Good luck!

---

