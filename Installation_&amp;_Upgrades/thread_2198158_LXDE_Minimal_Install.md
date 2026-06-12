---
title: "LXDE Minimal Install"
date: 2014-01-07
forum: Installation &amp; Upgrades
---

### Post by West Swan on 2014-01-07
Hello,

I have been using Linux for a little while now and thought it time to start having some fun with it.  I am doing this with Virtualbox.

What I am attempting is to build a light desktop environment similar to Lubuntu.

I started with the Ubuntu 12.04 alternate iso and selected "Install a Command Line System" 

Then I installed the following:[FONT=Symbol]              [/FONT]sudo apt-get install xorg lxde-core lxdm  and restarted.

Yay - I have a desktop environment I can use the terminal to install Synaptic, Firefox and whatever other programs I like.

Ok, so that is all good.  Internet (ADSL) works fine.  I haven't tried installing anything else yet but unless I'm missing something it should be fine.

When I am happy enough with how this is turning out, I intend to do the same on a couple of my old laptops.

[COLOR=#0000cd]I want to be able to plug usb drives into the laptops, connect the laptops to external monitors, printers etc and I want to use any proprietary graphics card drivers that are available.[/COLOR]

I think I can install [FONT=&quot]'ndisgtk'[/FONT][FONT=&quot] to access wireless networks through ndiswrapper,[/FONT] '   cups  '  to connect to printers etc.  I prefer a graphical to a command line interface so was basically seeing if anyone could recommend the easiest gui to do what is in blue above.

Because I have customised this install does that mean it is a new Distro :p


So yeah, at least on Virtualbox everything seems to be going good so far

This is fun!

Cheers,

Paul

---

### Post by Bucky Ball on 2014-01-07
What you want is this:

Minimal Install:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

It installs the Ubuntu kernel ONLY and you do the rest via 'sudo apt-get install' on a command line. In your case, you could do something like:
```

sudo apt-get lxde firefox thunderbird pcmanfm synaptic
```

... and whatever else you use. 

Even more fun! If you really want to bend your mind and go on a learning curve vacation, Linux From Scratch is for you:

[http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)

Have fun! ;)

PS: A remix or respin rather than a new distro I'd guess. Also, FYI, when you're happy with your creation you can create a bootable ISO of it using Remastersys. That way, you can install your masterpiece on any machine! ;)

---

### Post by ibjsb4 on 2014-01-07
Maybe you two should get together.

[http://ubuntuforums.org/showthread.php?t=2198071](http://ubuntuforums.org/showthread.php?t=2198071)

---

### Post by West Swan on 2014-01-07
> **ibjsb4 said:**
> Maybe you two should get together.

[http://ubuntuforums.org/showthread.php?t=2198071](http://ubuntuforums.org/showthread.php?t=2198071)


Thanks for that.  Yes I found the same UXTerm and Xterm after I had installed the command line system and then  [FONT=&quot]sudo apt-get install xorg  lxde-core lxdm

I then used Xterm to download LXTerminal which is much nicerer.

I tried the minimal cd at first but kept getting error messages (I can't remember what they were now) but I couldn't get it to work in virtualbox or vmware so used the alternate cd instead

So far so good :-)

Cheers,

Paul


[/FONT]

---

### Post by ibjsb4 on 2014-01-07
> I tried the minimal cd at first but kept getting error messages (I can't remember what they were now) but I couldn't get it to work in virtualbox or vmware so used the alternate cd instead

Strange.  This past year I have installed different flavors of ubuntu on different computers using the same mini.iso for all installs and not one fail.  Also use the disk.iso download for installing to vBox.  Nothing wrong with using the Alt-install CD, just strange.

---

### Post by Bucky Ball on 2014-01-07
I haven't tried the mini.iso in a vm, but oddly, I made an ISO of my minimal install with Remastersys and can't get that to boot as a vm. Perhaps I missed something when I installed that's preventing it from booting. It happens with these setups. I have no problem with the other dozen or so vms I play about with.

I mention it because might somehow relate to your problem with not being able to boot mini.iso in a vm, although I know plenty of others seem to be able to without issue. Perhaps it has something to do with the version of VirtualBox.

PS: Yes, use LXterminal myself, and PCmanFM. ;)

---

### Post by West Swan on 2014-01-07
Hello,

Ok, all the programs I wanted installed just fine and I've checked they are all working.

The exceptions are Synaptic and GUFW firewall gui.

I can open Synaptic but only through the command prompt (gksu synaptic).  If I click on the menu for Synaptic Package Manager nothing happens not even an error message.

With regards to the firewall GUFW.  When I click on the unlock button I get the error message 'wrong identification'

I have searched the forums for both issues but I'm not brilliant at searching.

Is it an easy fix?

Regards,

Paul

---

### Post by Bucky Ball on 2014-01-07
You're better off posting new threads for your new problems with descriptive titles and in the appropriate forum sections. This will improve your chances of help as they are off topic to this thread, buried seven deep and have nothing to do with ***Installations & Upgrades*** or the thread title. Good luck.

(This thread, in fact, isn't really a support thread.)

---

### Post by West Swan on 2014-01-07
Thanks Bucky Ball.

Will create another post.

Regards,

Paul

---

