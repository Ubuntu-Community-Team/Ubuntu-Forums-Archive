---
title: "Problem booting"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by afterburner on 2007-04-20
Hi, so I finally installed a clean Ubuntu 7.04, everything went smoothly...

It asked whether I wanted to restart, or continue using the live cd...I restarted, and everything appears fine until the Ubuntu logo appears with the progress bar....The bar BARELY starts loading and then simply stops. After waiting for a bit, a black screen comes up with the following message:

udevd-event[1937]: run_program: '/sbin/modprobe' abnormal exit

BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell(ash)

Enter 'help' for a list of built-in commands

/bin/sh: can't access tty; job control turned off

(initramfs)




any ideas?

---

### Post by cogadh on 2007-04-20
A lot of people are havig this problem, search the forum for "can't access tty; job control turned off"

Most of us are encountering it when we try to install, so we never get it to happen on a reboot. I have heard some people say that it is a random problem that only occurs every two or three boots, so you might just try a couple of reboots to see if it goes away.

---

### Post by Nobber on 2007-04-20
I have a similar problem with a clean install of Kubuntu 7.04. The progress bar on the splash screen gets nowhere.

Rebooted in recovery mode, and the kernel just hangs shortly after detecting the USB hub. I waited a minute or two for something to happen, but nothing did, so I rebooted using the magic SysRq key and I'm back in Edgy for the time being.

This is only on my machine at work, though; a few weeks ago I installed the Feisty beta on a laptop at home and it's been working OK.

Kind of annoying.

---

### Post by Nobber on 2007-04-20
Right, so I got Feisty to boot...with the Edgy kernel! I'm posting this right now on my hybrid Feisty/Edgy system, Which proves that networking still works, at least...

However, I suspect I'm asking for trouble in the long run, so back to Edgy/Edgy I go until this problem is properly resolved using only Feisty parts.

---

### Post by Nobber on 2007-04-20
Inspecting the kernel log from the Feisty/Edgy boot shows something interesting.

When I boot Feisty with the Feisty kernel, the last line I see on the screen is:

drivers/usb/input/hid-core.c: v2.6:USB HID core driver

and then the kernel hangs.

When I boot Feisty with the Edgy kernel, the NEXT line after that one is:

Adding 1052216k swap on /dev/disk/by-uuid/edbeb55a-cd57-4b66-8065-231eabb5d
b44.  Priority:-1 extents:1 across:1052216k

So it appears that Feisty/Feisty might be choking on the swap partition somehow.

I wonder if changing Feisty's /etc/fstab to use old-style /dev/sda? entries will fix the problem...

---

### Post by Nobber on 2007-04-20
And the answer is a resounding...NO!

:(

I really should stop talking to myself.

---

### Post by cogadh on 2007-04-20
You're not talking to yourself, we're all just quietly listening. This is good stuff, it's likely to help someone in the end.

---

### Post by ydoucare on 2007-04-20
> **Nobber said:**
> Inspecting the kernel log from the Feisty/Edgy boot shows something interesting.

When I boot Feisty with the Feisty kernel, the last line I see on the screen is:

drivers/usb/input/hid-core.c: v2.6:USB HID core driver

and then the kernel hangs.

When I boot Feisty with the Edgy kernel, the NEXT line after that one is:

Adding 1052216k swap on /dev/disk/by-uuid/edbeb55a-cd57-4b66-8065-231eabb5d
b44.  Priority:-1 extents:1 across:1052216k

So it appears that Feisty/Feisty might be choking on the swap partition somehow.

I wonder if changing Feisty's /etc/fstab to use old-style /dev/sda? entries will fix the problem...

I'm having the same problem after upgrading from the update manager...

---

### Post by rudeboyskunk on 2007-04-20
Ok, I had the same problem with booting that many of yall have had.  I switched over in GRUB to the recovery mode, so I could see where it would hang.  It stopped at the usb line like yalls, even after it found my usb keyboard and usb mouse perfectly fine.  A few times when I'd reboot it would do an additional line talking about firewire (all I remember is seeing "IEEE" before I got frustrated and took a figurative baseball bat to the computer), but it would still hang.  So, after about 3 more attempted reinstalls of Feisty (I always do clean installs rather than upgrades; I'm just quirky that way), it finally started working.  Whether or not it will work after a reboot I don't know, but here's hoping.

So my advice would be to just keep trying to reinstall until the developers or one of us comes up with a better solution.

And I'd like to say the only disappointment I have thus far is the absence of Mozilla Sunbird.  But other than that, another great job Ubuntu!

---

### Post by afterburner on 2007-04-20
I don't know if this is a fluke or not, but here is what I did, and it worked!

I don't know the technical terms, but here it goes...

You know how there are two cables that connect your hard drives/cd readers to your motherboard, the primary blue one, and a secondary one...When I had the problem in the OP, I had my hard drive connected to the primary cable (blue end) on the end of the cable as master, and a cd rom in the middle, as slave...

Then I connected the cd rom to the secondary cable (on the end, still as slave) and reinstalled Ubuntu...AND IT MIRACULOUSLY WORKED!

Once again, I don't know if this is a fluke or not, but I tried reinstalling the OS while I still had both the hard drive and the cd rom connected to the primary cable, and still had the problem. But when I did the above, and reinstalled, it worked.

---

### Post by cogadh on 2007-04-20
It was probably a fluke, but you should never have CD drives on the same cable/IDE channel as your hard drive, it slows down the hard drive performance.

---

### Post by mikexgough on 2007-04-22
I have the same issue, I have 2 machines and Upgraded via Upgrade manager............one machine (2hard drives - 1 ubuntu the other for data only) fine the other a dual boot with win2K , hangs on the splash screen for 2 mins then off it goes.........

---

### Post by Nobber on 2007-04-30
If anyone is still listening: I fixed the problem I had booting Feisty (where it would hang just after detecting the USB hub). Here's what I did:

1. Boot Feisty with an Edgy kernel.
2. Install linux-image-386.
3. Reboot and select kernel 2.6.20-15-386 in the grub menu.
4. Watch as Feisty actually boots with a Feisty kernel!

So while Feisty doesn't boot with kernel 2.6.20-15-generic, it does boot just fine with kernel 2.6.20-15-386.

Odd.

Anyway, I'm happy now!

---

