---
title: "Help! I'm So LOST!"
date: 2008-01-19
forum: Installation &amp; Upgrades
---

### Post by ajdudley on 2008-01-19
I have installed ubuntu, after running live cd, after reboot, i changed my resolution because i have a widescreen laptop. Continuing on, I proceeded to logout because i recieved a message after changning my res that i needed to log out before changes took effect. I logged out and received a blank screen. I then rebooted. After rebooting, I get the grub screen, and the ubuntu load screen (with the logo adn the load bar) however, that screen loads and then my comp screen goes blank! What do i do.

Hardware
HP Pavillion dv6000 notebook
Processor: AMD TURION 64 X2 1800MHZ

---

### Post by skulda on 2008-01-19
I think the resolution you have chosen isn't supported by your laptop.
Try pressing ctrl-alt-f1 and log in. Then edit /etc/X11/xorg.conf (as root, e.g. enter sudo vim /etc/X11/xorg.conf) and adjust the resolution.
skulda

---

### Post by ajdudley on 2008-01-19
im sorry, im so dumb. How do i do all that? when do i press ctrl alt f1?

---

### Post by skulda on 2008-01-19
Hi!
when your screen goes blank, hit ctrl + alt + f1 at one time.
Then you should get a screen allowing you to login with your username and password to a terminal.
Then enter
```
sudo vim /etc/X11/xorg.conf
```
and look for 'section screen'
Somewhere in this section it should say 'modes' and some resolution (eg 1280x800)
Press a to enter the insert mode and replace the resolution with a resolution you want or know to work for your laptop.
Then press esc and enter ":wq" to save the file and exit vim.
Reboot by entering "sudo reboot"
Hope that helps
skulda

---

### Post by ajdudley on 2008-01-19
sry again. I tried pressing ctrl+alt+f1 however, nothing happened. After the load screen it flasheed that erroro again but i cant read it.

---

### Post by skulda on 2008-01-19
What happens if you press ctrl-alt-backspace? This should shut-down your x-server...

---

### Post by ajdudley on 2008-01-19
here are the errors i recieve

error recieving uevent message: no buffer space available

dsdt.aml not found

and a couple others that go by to fast to read

right now it is frozen on a screen with several things on it that look similar to this
these are the last seven, i can give you the rest if you need...

[    0.524000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.524000]CPU:L2 Cache: 512K (64 bytes/line)
[    0.524000] CPU 1(2) -> Core 1
[    0.524000]Cpu1:AMD Turion(tm) 64 X2 Mobile Technology TL-56 stepping 02
[    0.524000] Total of 2 processors activated (7236.08 BogoMIPS).
[    0.524000] Enabling 10-APIC IRQs
[    0.524000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pi2=-1

---

### Post by ajdudley on 2008-01-19
again, blank screen

---

### Post by GavinZac on 2008-01-19
its actually ctrl+alt+F2 you should be pressing.

---

### Post by ajdudley on 2008-01-19
ctrl+alt+f2 doesn't work either...

---

### Post by skulda on 2008-01-19
Mhh...the errors look like something is wrong with your acpi, but that should not cause the problem...

A different thing you could try is to boot from a live disk (ie your install disk), open a terminal, mount your harddisk and then edit xorg.conf...
```

sudo -s
mkdir mnt
mount /dev/sdaX mnt
vim mnt/etc/X11/xorg.conf

```
Replace sdaX with the adress of your harddisk
Skulda

---

### Post by ajdudley on 2008-01-19
first of all, it doesn't allow me to boot from live disc either
second, i didn't understand any of the rest of that. I downgraded from vista cuz it sux ballz, and ive never used linux before...

---

### Post by wolfen69 on 2008-01-19
[https://help.ubuntu.com/](https://help.ubuntu.com/)

---

### Post by skulda on 2008-01-19
That's strange. Didn't you say you installed from a live cd? Inserting this cd and trying to boot doesn't work?
If that's the case, i fear that the problem is beyond my knowledge...sorry
Skulda

---

### Post by ajdudley on 2008-01-19
thanks neways

---

### Post by GavinZac on 2008-01-19
> **ajdudley said:**
> first of all, it doesn't allow me to boot from live disc either
second, i didn't understand any of the rest of that. I downgraded from vista cuz it sux ballz, and ive never used linux before...

When your computer is coming up, GRUB should give you the option to press a key to boot from the CD.

---

### Post by xfearxnxloathing on 2008-01-19
honestly if the live cd isn't booting and your previous install isn't either, it seems quite possibly your harddrive is crapping out.  

my 200gig crapped out on me the first linux go around but linux wasn't to blame, it was already doing this with windows before the linux install.  i thought it was windows causing the problem but when i made the switch everything checked out ok and the drive read no errors.  it would boot half the time...  when it wouldn't reboot i got all kinds of weird screens, including the blank (black screen).  it would hang on normal screens as well.  i took out the drive and put in another installed fresh from the live cd and everything is all good.  if you have another drive for the laptop lying around i would try that if you dont ever find any other solutions.  one way you can be sure it's the drive, when you first boot hit delete and go to boot options and see if the harddrive is even showing up.  also, if it is make sure it's selected as first boot device and that cd-rom is selected as the second.   

if you want to try a fresh install, do the same but select cd-rom as first boot device and live cd should work.

hope it's not the drive, goodluck!

---

### Post by GavinZac on 2008-01-19
> **xfearxnxloathing said:**
> honestly if the live cd isn't booting and your previous install isn't either, it seems quite possibly your harddrive is crapping out.  

my 200gig crapped out on me the first linux go around but linux wasn't to blame, it was already doing this with windows before the linux install.  i thought it was windows causing the problem but when i made the switch everything checked out ok and the drive read no errors.  it would boot half the time...  when it wouldn't reboot i got all kinds of weird screens, including the blank (black screen).  it would hang on normal screens as well.  i took out the drive and put in another installed fresh from the live cd and everything is all good.  if you have another drive for the laptop lying around i would try that if you dont ever find any other answers.  one way you can be sure it's the drive, when you first boot hit delete and go to boot options and see if the harddrive is even showing up.  also, if it is make sure it's selected as first boot device and that cd-rom is selected as the second.   

if you want to try a fresh install, do the same but select cd-rom as first boot device and live cd should work.

hope it's not the drive, goodluck!
If his hard drive had died, he would be stuck on GRUB with error 21.

---

### Post by xfearxnxloathing on 2008-01-19
> **GavinZac said:**
> If his hard drive had died, he would be stuck on GRUB with error 21.

funny i never got error 21 nor did any errors ever get reported when checkdisk.  if the arm is broken inside the drive it wont show that the harddrive is the problem.

---

### Post by dagrnd1 on 2008-01-20
Ok, so this guy is in the same block that I am.  Nothing is physically wrong with his computer, it is the firmware of the wireless card.  I am having the same issue, and if you take a closer look at the text scrolling on the screen, before your screen goes blank, you will see this error message twice: "BCM43XX Microcode  blah blah...fw Failed", which means the firmware cannot load in Ubuntu. 

Now, I am having the same issue and all of the sources I find are too technical, so if anyone can break downt he whole ndiswrapper, and firmware fix(and what it does), that would be great.  I am personally doing a dual boot, so I'd rather not ruin anything on the windows end.

Thanks

---

### Post by xfearxnxloathing on 2008-01-20
you guys make this too hard.  unless you have precious amount of apps you'd have to reinstall that would take 2 days to complete, why not just do the simplest half-hour fresh install?

---

