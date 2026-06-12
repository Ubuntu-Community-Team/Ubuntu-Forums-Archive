---
title: "Some automatic update(s) messed up my computer (Gnome)"
date: 2010-06-03
forum: Installation &amp; Upgrades
---

### Post by bmathise on 2010-06-03
Hi,
I have had Ubuntu 9.10 for 6 months, and it worked like a charm. Then I decided to upgrade to 10.04 because it is Long Term Support. I upgraded using the software upgrade tool. So far so good. When I rebooted my old computer, it wouldn't run the new kernel, so I was stuck with the old one from 9.10. OK, this worked, and I was sort of satisfied. Then, about a week ago, I ran some automatic updates and rebooted (not a required reboot). After that I could only get the CLI to work. Gnome (or gdm) will absolutely not start. I tried to install Kubuntu-desktop to see if that would work, and it does. I can use KDE, but I don't like it and would like to have Gnome back.

I can't remember which updates made the mess. Are there any logs I can check?

The new kernel(s) just will not boot. I can't boot from the 10.04 live CD. It halts after showing the Ubuntu logo with 4 dots (progress bar). After that nothing happens. When I boot the old kernel (2.6.31.20-generic), I get these messages, among a heap of similar messages:

> 
[29.218139] end_request: I/O error, dev sr0, sector0
[29.702008] via686a 0000:00:04.4: base address not set - upgrade BIOS or use force_addr=0xaddr
[92.344017] BUG: soft lockup - CPU#0 stuck for 61s! [events/0:6]
If that is of any help.

I dual boot Ubuntu and Windows 2000. Windows boots fine. Grub works fine. I can boot  from Slax, DSL and Debian Live CDs without problems. I no longer have the 9.10 Live CD (gave it away to someone who needed it more than me ... ). When I try to download the 9.10 CD image, I can boot from it, but I need username and password to log in (what the ...!!)

I would really like to get my primary OS with Gnome back, because I'm not going back to Windows and I will not be using KDE. Both feel like a strait jacket compared to the relaxing and easy-to-find-things Gnome.
Thanks for any help :)

Bjorn

---

### Post by mrinehart93 on 2010-06-03
Is the 10.04 you're trying to use x86 or x64? I just mention that because I see that the error message is telling you to upgrade the BIOS on your motherboard, which leads me to believe that your CPU doesn't support x64 and that you need a newer BIOS. I may be completely wrong though, so take my guess with a grain of salt. It was just a shot in the dark.

---

### Post by dino99 on 2010-06-03
there are some issues with plymouth and removing [COLOR="Red"]splash[/COLOR] on the boot line often help, and add [COLOR="Blue"]force_addr=0xaddr[/COLOR] as its needed

if you dont see the grub menu , at end of bios process, hold "shift" key down to see it, edit the boot line (e), make the changes, then boot (x)

---

### Post by acrazyplayer on 2010-06-03
Thats kinda strange, try typing "sudo apt-get install ubuntu-desktop" also you could get rid of almost everything kde by going here [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by bmathise on 2010-06-03
mrinehart93: I use 32 bit x86. My computer is about 10 years old and has an AMD Athlon 900 MHz CPU and 1024 MB RAM. 

acrazyplayer: I tried that. All I get is that I already have the latest packages. And, yes, I ran sudo apt-get update first :). Getting rid of KDE won't be a problem. I just want Gnome back. Thanks for the tip, though.

dino99: I'll try to remove splash and see if that works. I assume you are talking about Grub? I do see the Grub menu, and I use it to dual boot between Ubuntu and Win 2k. Where should I add [COLOR=Blue]force_addr=0xaddr[/COLOR] ? Instead of splash ?[COLOR=Blue][/COLOR]

---

### Post by bmathise on 2010-06-03
[LEFT]I didn't find any splash in the Grub menu. There was a reference to quiet splash (I think it was) and after each menuitem there was a line that said [COLOR=Blue]quiet[/COLOR]. Does that have anything to do with it?
And where should I add [COLOR=Blue]force_addr=0xaddr[/COLOR]?[COLOR=Blue][/COLOR][/LEFT]

---

### Post by bmathise on 2010-06-04
> 
[29.218139] end_request: I/O error, dev sr0, sector0
[29.702008] via686a 0000:00:04.4: base address not set - upgrade BIOS or  use force_addr=0xaddr
[92.344017] BUG: soft lockup - CPU#0 stuck for 61s! [events/0:6] 			 		


Fotgot to say, I get these mesages when I boot kernel 2.6.31.20-generic. It does boot, but it boots into the command line. Gnome won't run, but I can start KDE. This kernel, and Gnome, worked fine until I installed some automatic updates. The problem is most likely related to these updates. I can't remember which applications were updated. Are the any logs I could check?

---

### Post by bmathise on 2010-06-05
No ideas? Anyone know where I can download a 9.10 iso-file that doesn't require me to log in, so I can make a fresh install? I already tried to download from the Ubuntu archives 3-4 times, but for some reason, I need username and password to log in when I boot the live CD. The 10.04 CD will not boot on my 10 yrs old computer (that is, the new kernels won't boot, 2.6.31-20 boots), so unless something changes, it seems that 9.10 is end of the line for this computer. Which is a bit sad, but I can live well with 9.10.

The only other alternative for me is to go hunting for another distro, but I'm reluctant to take that step. Ubuntu is my number 1 choice.

---

### Post by acrazyplayer on 2010-06-05
Most distro passwords are u.n. "guest" p.w."guest" and u.n. "root" p.w."root"

you could also try u.n. "ubuntu" p.w. "ubuntu" 

also try not typing anything at all for at least a minute. sometimes they auto login but if you start to type they stop and assume you know the password.

---

### Post by acrazyplayer on 2010-06-05
Also you add the "force_addr=0xaddr" to here, enter in terminal  

"sudo gedit /etc/default/grub" then find where it says "quiet splash" and add it to the end, you could also try adding "nomodeset" to the end, deleting the word splash and/or quiet.

---

### Post by bmathise on 2010-06-05
Thanks acrazyplayer, I'll try that. Should I add [COLOR=RoyalBlue]force_addr=0xaddr[COLOR=Black] as is or should I enter an address instead of [COLOR=RoyalBlue]0xaddr [COLOR=Black](e.g. force_addr=0xf000)?

I also tried all the passwords you suggested. I even tried the usernames and blank passwords. What happened to the 9.10 live CD? The one I had would boot without asking for login. But, I will try your suggestion about waiting in case it will auto login.
Just a little detail, I have to use nano instead of gedit because I only have the command line, but that's OK, though.
[/COLOR][/COLOR][/COLOR][/COLOR]

---

### Post by bmathise on 2010-06-05
There was no /etc/default/grub so I tried to enter the options to the kernel line in /boot/grub/menu.lst instead. The result was the same as before.
I will now try to boot the 9.10 live CD and wait to see if it will auto login.

---

### Post by bmathise on 2010-06-05
Nope. It didn't auto login. I also tried all the cominations of usernames and passwords I could think of with no result. I guess I have to borrow the old CD back on Monday.

---

### Post by acrazyplayer on 2010-06-05
That's all interesting, with your first question I'm not entirely sure but I would assume you just leave it as is "force_addr=0xaddr" how else would you know the correct address. 

and as for the password situation I just read this, when it is asking you for a password on the live CD 

"Shift-ctrl- F1
sudo passwd ubuntu

type a new password

Shift-ctrl-F7

now login with username ubuntu and your new password"

I though it was "control+*alt*+F1" but maybe it used to be shift.

---

### Post by bmathise on 2010-06-05
Thanks again :) I'll try that right away.

---

### Post by bmathise on 2010-06-05
It didn't work. Nothing happened. I even tried several other key combinations, Shift+Ctrl, Alt+Ctrl, Shift+Alt+Ctrl, Alt+Shift and F1 through F12. Nothing. 

I also booted into the command line from the HD and tried 
> 
sudo apt-get --reinstall install gdm

Gdm was reinstalled, but won't run.

---

### Post by acrazyplayer on 2010-06-05
Okay, apparently and obviously this password to use livecd is some sort of bug that most blame on either the cd itself or the method of burning the cd. So if possible try using a usb stick instead of a cd. Unetbootin works great.

---

### Post by bmathise on 2010-06-14
OK, I haven't had time to look more into this. I have been stuck with Windows 2000 until now (and still am). 

But, I have managed to snatch a few more error messages off the screen before they scroll off the screen.
The very first one is this:
> 
mounted none on /dev failed: no such deviceea2e24d9d5
ACPI I/O resource vt596_smbus [0xe800-0xe807] conflicts with AGP region SM00 [0xe800-0xe806]
via686a 0000:00:04.4: base address not set - upgrade BIOS or use force_addr=0xaddr 


My motherboard is Asus A7V ACPI BIOS Rev 1004
I have disabled everything I could find in BIOS that had to do with power management.

I can only boot kernel 2.6.31-20-generic. Anything newer halts. Gnome refuses to start. I have tried startx but it doesn't help. If I choose to use KDE, the KDE login screen comes up as normal, I can log in and KDE runs as normal. 

I have ordered CDs with 9.10 and 10.04 from Canonical to make sure I have good CDs at least. They haven't arrived yet, perhaps they will tomorrow or Wednesday.

Anyone got an idea?

---

### Post by bmathise on 2010-06-20
OK, I got the CD's from Canonical and none of them will boot. The 10.04 CD just freezes while showing the Ubuntu logo with 4 dots underneath. The 9.10 CD comes up with a green screen and that's it. I haven't tried them on another computer, but I doubt that all ten CD's are faulty
The weird thing is that I can my existing Ubuntu 10.04 installation if I want to use KDE. No problem (except that I'd much rather have Gnome). I can also boot up many other OS's like Windows 2000, DSL, Slax, Linux Mint and Debian. I was a bit surprised when I saw that I can boot up Debian with Gnome, but not Ubuntu with Gnome. If I try startx X will try to start, but after a while it gives up and falls back to the command line

The error messages seem to indicate an address conflict between ACPI and my AGP graphic card. Could it be a problem with Nvidia driver? Is there a safe way for me to uninstall the Nvidia driver and see if that will help? I can always reinstall it later.
Or maybe somebody have other suggestions?

---

### Post by firemane on 2010-06-20
I am having a similar problem after an update I made this week. The linux kernel was updated among other things, I believe.

I am using a Gigabyte motherboard, a bit more advanced than yours. I tested all the hardware and it is all in working order. My machine is a clean install, Ubuntu as the sole OS, well above the minimum specs. No GRUB involved. 

Most of the time the machine simply hangs halfways through the OS booting process and all I see is a black screen with no cursor. On one out of every 10 attempts or so the machine boots all the way and I can use Ubuntu without problems. 

Once I saw a detailed, step by step booting and the machine just hung there. Unfortunately I could not copy or print what was displayed on the screen. 

Is there a way to see a detailed booting or to see a log of the booting process? This may help me diagnose where the problem may be.

---

### Post by bmathise on 2010-06-23
As it seems to be a conflict between ACPI and AGP, is there a possibility that removing the NVIDIA driver would help? How do I do that from the command line?

What do I lose if I switch from Ubuntu to Debian? Because Debian with Gnome will boot without errors. Could that switch be a good temporary solution? I say temporary, because I really like Ubuntu and would like to continue to use it. But, when I can't make it boot, I'm stuck with Windows 2000, which can't read my large ext3 harddrives.

---

### Post by bmathise on 2010-06-25
Hello Debian. Now it works.

---

### Post by bmathise on 2010-06-29
YESSS! It looks like I'm back to good old Ubuntu. I have no idea how.

I have been booting into the command line (which was available all the time) regularly to update the installation. I did that today, too. Then I tried (again) to replace "quiet splash" with "nomodeset=1" on the kernel line (kernel 2.6.31.20 from Ubuntu 9.10), and voila, the computer suddenly decided to boot into low graphics mode. I copied back the backup of my /etc/X11/xorg.conf file and rebooted, this time without the nomodeset=1 setting, but with "quiet splash" removed (as it has been for a long time). The computer booted up very normally, everything seems to work as normal.

So, now I can ditch the Debian installation and get back to using my preferred OS, Ubuntu with Gnome. On second thought, maybe I should wait a couple of days before I delete Debian :p

Perhaps the newer kernels will start to boot as well, given some time ;)

---

