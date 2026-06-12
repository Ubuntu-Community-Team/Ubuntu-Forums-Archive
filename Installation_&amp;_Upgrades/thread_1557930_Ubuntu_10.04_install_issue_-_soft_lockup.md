---
title: "Ubuntu 10.04 install issue - soft lockup"
date: 2010-08-21
forum: Installation &amp; Upgrades
---

### Post by john_mc on 2010-08-21
[LEFT]Hi All, if I am in the wrong palce then apologies and refer me on.

I have been tinkering with Linux and a afirend advised me to install ubuntu server and liking but still a relative noob that can't find the answer to my problem - which is surprising as folk have some really good advice, guides, etc.

I have been running ubuntu server 9.04 on my PC and installed the GUI with sudo apt-get install ubuntu-desktop.
I then upgraded to 10.4 throught the gui and still no problems 

ARecently my mate gave me an ATI X800 so I could get dual screens running as I couldn't do it on my current ATI 9600. I swapped the cards and after the GUI install I get the error. 

Anyone know how to fix this?
BUG: sOFT lOCKUP - CPU#0 Stuck for 61s! [Plymouthd:344]

I have switched back to my old card - same error

HELP HELP as there is blood on the wall from me banging my head on it.

Thanks in advance folks[/LEFT]

---

### Post by dino99 on 2010-08-21
boot into recovery mode (no quiet or splash) to see what happen.
when you get the command line , run:

sudo rm -f /etc/X11/xorg.conf

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

reboot

if you succeed then add x-swat ppa to synaptic repo tab:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

update again, remove/purge (right click) the ati driver installed then reinstall the x-swat packages

---

### Post by john_mc on 2010-08-21
Thanks for the quick reply Dino99,

At present I can't boot into recovery mode as I don't get the Grub loading screen. When I switch my PC on the usualy screen appears with system details and the screen blinks once/twice, then the first thing I see is text from loading that halts on

"Unexpectedly disconnected from boot status daemon"

which then goes to 

"Mounted filesystem with ordered date mode"

The system then either sits ate a flashing cursor or continues to log in. In continually pressing Esc doesn't do it will continue to tinker and google to get around this.

Any other suggestions are welcome.

---

### Post by john_mc on 2010-08-21
I got the recovery mode by holding "shift" on booting but the recovery mode stopped at a flashing cursor. I decided that it was corrupt from reading forums and did another reinstall.

Installed ubuntu server 10.04 and when booting I get,
Grub ;pading
error: No such disk

Then proceeds to login prompt

Before isntalling the GUI I launched the recovery mode and don't see Grub 2 like I see around the forums and wiki. My recovery console has;

ubuntu linux 2.6.31-14-generic-pae
ubuntu linux 2.6.31-14-generic-pae (recovery mode)
Memory test
Memory test serial console

Is this the problem or is it that when I install the GUI Grub doesn't know where it is installed? Any advice to avoid another reinstall

---

### Post by john_mc on 2010-08-21
I am still getting the Grub error: no syck disk and boot to logon prompt

I have changed my BIOS settings so the HDD is the primary boot device and disabled/everything else I can think off and find on the forums. I don't see athis being a problem as I am not running a dual boot and my setup worked before.

ran sudo apt-get install grub2 but after cheking the recovery mode it doesn't show the grub2 kernel like I have seen on other posts. I still have;

ubuntu linux 2.6.31-14-generic-pae
ubuntu linux 2.6.31-14-generic-pae (recovery mode)
Memory test
Memory test serial console

I then ran;
sudo apt-get update
sudo apt-get install ubuntu-desktop

Will let you know and wlecome any comments.

---

### Post by john_mc on 2010-08-21
right so I finally for ubuntu server 9.04 installed and working fine with no hardware changes to my system. I ran the upgrade to 10.04 and upon restart it get the same error with the CPU soft lockup.

After holding shift I jumped into the recovery menu and see some new entries so it now looks liek this;

ubuntu linux 2.6.32-24-generic-pae
ubuntu linux 2.6.31-24-generic-pae (recovery mode)
ubuntu linux 2.6.31-14-generic-pae
ubuntu linux 2.6.31-14-generic-pae (recovery mode)
Memory test
Memory test serial console 


In testing;
ubuntu linux 2.6.32-24-generic-pae - does not load GUI
ubuntu linux 2.6.31-14-generic-pae - works fine

I realise i am far from an experienced linux user but it looks like a GRUB error and looking for some comments on how to fix/advice why it happens?

Going to google around some more about editing the kernel for the system to boot on. Hope this is helping someone that is in the same place as me.

---

### Post by mörgæs on 2010-08-22
Is there a particular reason that you are reinstalling 9.04 and then upgrading to 10.04? Have you tried installing 10.04 directly?

---

### Post by john_mc on 2010-08-23
Yeah mate whenever I install Ubuntu 10.04 directly I rebooted and get the command line. After this i isntall the desktop and after a reboot can't get past the soft lockup error.

The only way i am working at the moment is holding shift and booting using ubuntu linux 2.6.31-14-generic-pae instead of ubuntu linux 2.6.32-24-generic-pae.

I have tried running sudo apt-get install grub-pc

Any ideas?

---

### Post by mörgæs on 2010-08-23
No, sorry. There are a lot of hits in Google for the soft lockup error, but they don't seem to fit this problem.

If you install 9.10 and then update to 10.04 you will be in the Grub2 family and not in Grub. I doubt that this will solve the problem, though...

---

### Post by john_mc on 2010-08-23
Agreed, the answer is not easily found in Google.

I used,

Sudo apt-get install grub-pc

Think i have grub2 installed but doesn.t work and not starting to wonder back to my XP machine as it just works. 

Thanks for the comment but i think i will find myself on the business end of a shotgun with this problem, lol.

---

