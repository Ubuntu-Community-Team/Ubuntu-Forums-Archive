---
title: "Gutsy will not boot... back to windows unless YOU can help"
date: 2007-11-12
forum: Installation &amp; Upgrades
---

### Post by Kevanx on 2007-11-12
I'm in dire straights here. I'm a couple of steps above noob, but I'm way over my head on this one. Any help greatly appreciated.

1. Love Ubuntu. Upgrade from Edgy->Feisty was fine back in April, and finally tried to update to gutsy last week.
2. Update froze first time, then rolled back. Went perfectly the second time.
3. Restarted to a black screen.

I know this problem has been documented, but I don't think it's the same issue.
When I restart, the "UBUNTU" loading screen appears after grub selector, the orange bar loads completely, then disappears. **The Gnome desktop NEVER appears, neither does any splash screen**.

Booting up in safe mode, I appended vga=791 to the line starting with 'kernel' in /boot/grub/menu.lst as per the instructions here:
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen"). The only difference was that now there is a single flashing cursor line instead of a completely black screen. Disk activity continues for ages after boot.

Ideally, these would be my choice of solutions, in order:
1) A fix to the problem so I can run gutsy.
2) A system restore to Feisty.
3) A clean install of Feisty.
My problems:
1) I switched to ubuntu because I could no longer get my windows home network to function. It still doesn't, so I don't know if I am able to do a network install.
2) My CD/DVD rom won't read CDs/DVDs anymore (piece of crap Toshiba Satellite 1800 ~ 6 years old), which makes a CD install impossible.

Annnnnnd BREAK!

Cheers,
Kevan

---

### Post by bobyy on 2007-11-12
Hy don`t panic :) 
After "...is a single flashing cursor line.." apearing hit ALT+F1...for me it was working..

---

### Post by gsiliceo on 2007-11-12
You need to start in recovery mode and then 
dpkg-reconfigure xserver-xorg
and when asked remove any resolutions your screen/graphic card does not support.
Restart

---

### Post by Kevanx on 2007-11-14
Heh. Don't Panic, indeed.
The ALT+F1 fix did not help me out.
Tried the dpkg-reconfigure xserver-xorg, and when I got to the dialogue about autodetecting the monitor configuration, the screen goes permenantly dark, just like on startup. Choosing "no" for autodetect associates the Identifier to be "Generic Monitor".

gsiliceo, you hit the nail on the head, it appears. Now I'm going to try and find a solution to that, because it definitely seems to be a xorg monitor issue. Thank you both so much for the prompt responses. Any further help still appreciated.

---

### Post by MadmanMike83 on 2007-11-14
in the reconfigure menu what driver does it autodetect?

I had a similar problem when I stuck with ati drivers.  Switching to the 'vesa' option and installing a few lower resolutions seems to have fixes the problem.

---

### Post by Saint Angeles on 2007-11-15
reboot into recovery mode and edit your /etc/usplash.conf 

make x= "your resolution width" and y="your resolution height"
reboot and see what happens

---

### Post by Kevanx on 2007-11-21
I had tried editing the usplash previously, and the xres and yres were spot on. Just for a kick I tried reducing them from 1024x768 to 800x600, and that didn't solve anything.

I don't have an ATi card, it's a noname crappy graphics card (Trident cyberblade).
In the xserver-xorg reconfigure menu (under recovery mode), it autodetects trident, which seems right, and the identifier is Trident Microsystems CyberBlade/i1, perfect, again. 1024x768, 800x600, and 640x480 are all enabled by default.
Another strange thing is that the monitor identification that it offers is "Generic Monitor" instead of a brand and model. Switching to vesa did not work either.

I greatly appreciate all the help. I'm still at wit's end, and had forgotten how buggy my version of XP had gotten to be, until I had to start using it regularly.

Any more help out there? I'm convinced there's a solution somewhere...

---

### Post by Kevanx on 2007-11-22
I think I'm out of luck on this one. Maybe I need to buy a computer that can actually run gutsy. It's sad to have to say that about any linux distro, though...

---

### Post by -grubby on 2007-11-22
> **Kevanx said:**
> I think I'm out of luck on this one. Maybe I need to buy a computer that can actually run gutsy. It's sad to have to say that about any linux distro, though...

if Feisty worked (unless I am wrong) then why not go back to it?I think I'm out of luck on this one. Maybe I need to buy a computer that can actually run gutsy. It's sad to have to say that about any linux distro, though...

---

### Post by Kevanx on 2007-11-24
Regarding going back to Feisty, that would be fine, and was one of my questions in the original post - I don't know how to go back to feisty because my CD drive doesn't read any more, and I looked into a network install, but it's over my head.

---

### Post by shamasis on 2007-11-24
I am a Windows developer for the past 4 years. I am relatively new to Linux (hence might have some 'jargon' related problems while communicating with you!). However, I have had same issues during my Gutsy installation.

If you have a working command prompt waiting, try moving to runlevel 3 by typing "telinit 3".
Miraculously, running xorg in this way had solved my problem, while trying anything from recovery-mode did not solve any issue.

If you happen to reach your GUI in this process, try to reconfigure xserver the way u were doing earlier.

In my opinion, "Generic Monitor" should make no display issue. Recognizing a monitor's brand does help only when your OS cannot communicate with your graphics card to retrieve the monitor capabilities. It must be an issue with your graphics driver.


PS: Pardon me (pro linux users) if I sound dumb. As you can see these are my first foray into Linux world and I am simply loving the "humane" part of being a human.

---

### Post by Kevanx on 2007-11-24
Thank you, but trying to type in "telinit 3" didn't work. I even tried to open up a terminal as though I were in gnome and my monitor were simply broken, but it didn't do anything. Also, the beauty of linux is that there really are no stupid questions. Linux pros are in my experience, much more approachable than other OS fanboys and fangirls, because they had to teach themselves too!

I finally managed to get the live CD running, so I went ahead and reinstalled from v 6.06. I think I'll stick with feisty until I replace this old piece. Thanks so much to everyone for your help.

---

