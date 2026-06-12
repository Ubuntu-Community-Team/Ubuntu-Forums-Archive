---
title: "Please help -- trouble installing on HP Pavilion dv6-2044el"
date: 2010-06-26
forum: Installation &amp; Upgrades
---

### Post by jorgengb on 2010-06-26
Hi,

I am trying to install Ubuntu 10.04 on my laptop, a rather new HP  Pavilion dv6-2044el. Windows 7 is already installed, so I've tried "installation inside Windows".

I have been using Ubuntu for at least a couple of years, and this is the first time there is no way to complete an installation :confused:: The process halts after restarting the system.

A few months ago I managed to install Ubuntu 9.10 on this laptop without any trouble, before disinstalling it.

I have tried:

[LIST]
[*] *ubuntu-10.04-desktop-i386.iso*
[*]* ubuntu-10.04-desktop-amd64.iso*
[/LIST]
 both from 

[LIST]
[*]a CD and
[*]an USB flash drive,
[/LIST]
always with the same frustrating result.

I tried also to install 9.10 first and then upgrade to 10.4, but the upgrade didn't work either.

Today I even tried Maverick Meerkat (maverick-desktop-i386.iso) from a USB flash drive, but it also halted during the process.

I would really appreciate any suggestions !

Jorgengb

[tags: HP, Hewlett Packard, Pavilion, 2044el, Lucid Lynx, Maverick Meerkat]



[FONT=Arial Black]Additional info:[/FONT]

When booting from USB drive with Maverick Meerkat:
UNetbook
Default

then I get the following message with a flashing underscore after it, and nothing more happens:
**[COLOR=Red]FATAL: Error inserting ramzswap [...]  Unknown symbol in module, or unknown parameter (see dmesg)[/COLOR]**


When running Wubi on a USB drive with Maverick Meerkat:
after a while, the installer says **[COLOR=Red]"Installing Ubuntu-10.04"[/COLOR]** and starts to download *ubuntu-10.04-desktop-amd64.iso.torrent*
(Why? The more recent Maverick Meerkat should already be on the USB drive, and anyway I didn't start from a 64 bit Meerkat but from *maverick-desktop-i386.iso*).

---

### Post by bcbc on 2010-06-26
The latest wubi.exe checks which version is correct for your computer - unless you override it - and will download and install this version instead. In your case it's 64-bit 10.04 (it's not going to consider an alpha OS for obvious reasons). As I said, you can override this but...

Running Maverick because you can't get a 'stable' release to work (10.04) is not good idea, unless you are prepared for crashes and consider your computer a 'test system'. i.e. don't care if you lose all your data.

I did a quick google it looks like there are some issues with your computer and linux. e.g. [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=571251](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=571251) 

I haven't found a fix, but maybe if you search hard enough. Or you could use 9.10 until someone figures it out.

Good luck

---

### Post by jorgengb on 2010-06-27
Thanks for your suggestion, bcbc!
Well, actually I do need a stable computer -- this Pavilion is where I have «all my daily life», and I can't take any risks.
I think the best thing I can do is to install 9.10 without upgrading to 10.4, until someone finds a workaround or those at Canonical fix the problem. Oddly enough, 10.4 works fine on another, much older laptop I have (an Acer Travel Mate 4000 bought in 2003) and on my netbook (Eee PC 900).

So far I have just tried to install inside Windows, I was wondering whether installing on another partition might solve the issue (probably not, as I can't even run 10.04 from a CD or USB flash drive).

---

### Post by bcbc on 2010-06-27
Installing direct is a good idea, but won't make a difference in this case. 
But I was reading that bug report again and it seems the problem is with ACPI.

Did you try the 10.04 live cd with acpi=off ? I think you press F6 after the language selection.

If you can get it to work, then at least you can upgrade to the latest kernel were there may be a fix.

---

### Post by jorgengb on 2010-10-15
Now that 10.10 has come, I decided to give it a try, rather confident that everything had been fixed by now. Nope. Same problem when trying to install Ubuntu from Wubi.

Suggestions are welcome, before I give up as a Ubuntu user...

---

