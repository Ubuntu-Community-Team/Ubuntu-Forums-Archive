---
title: "Installation - CPU = P3, Ram=192MB"
date: 2011-04-02
forum: Installation &amp; Upgrades
---

### Post by dobber1978 on 2011-04-02
Any recommendation on what I can install on an older laptop computer?

The computer is an old Dell machine that currently runs win98. I would like to move this machine out to the garage so that I can access manuals and service bulletins.

The machine states that it has 192MB of ram and I think it's a 500MHz PIII CPU.

Currently it doesn't have a wireless network card but I would like to install one so recommendations here would be great as well.

Thanks
Jeff

---

### Post by ojdon on 2011-04-02
Ubuntu-wise, the [lubuntu]("http://lubuntu.net/") version is going to be your best bet running on that machine. If it doesn't run well you might want to look at a Puppy Linux flavour.

---

### Post by Joe of loath on 2011-04-02
Lubuntu will work, but replace chromium with midori as a browser, as chromium is too heavy.

---

### Post by mörgæs on 2011-04-02
If you have Windows 98, it is more than likely that you have a virus. Best is to format as soon as possible.

Chromium is only heavy with many windows open. I have a similar machine, and it runs a one-window Chromium with a decent speed. 

Remember to install Flashblock.

---

### Post by Joe of loath on 2011-04-02
> **mörgæs said:**
> If you have Windows 98, it is more than likely that you have a virus. Best is to format as soon as possible.

Chromium is only heavy with many windows open. I have a similar machine, and it runs a one-window Chromium with a decent speed. 

Remember to install Flashblock.

Yes, but midori will run multiple windows at the same speed ;)

---

### Post by Simba7 on 2011-04-02
> **mörgæs said:**
> If you have Windows 98, it is more than likely that you have a virus. Best is to format as soon as possible.

Chromium is only heavy with many windows open. I have a similar machine, and it runs a one-window Chromium with a decent speed. 

Remember to install Flashblock.
No format, shred. One pass should be enough (shred -v -n 1 /dev/sda). That way the drive is clean from beginning to end.

---

### Post by dobber1978 on 2011-04-03
And no issues with opening PDFs with Lubuntu??

---

### Post by Dutch70 on 2011-04-03
Lubuntu uses Evince, it should work fine for opening PDF's. You can always test it from the live cd/usb. Although it will be slower.
[[COLOR="RoyalBlue"]https://wiki.ubuntu.com/Lubuntu/Applications[/COLOR]]("https://wiki.ubuntu.com/Lubuntu/Applications")

---

### Post by mörgæs on 2011-04-03
You can just add an alternative PDF reader from the repositories, if you don't like the default one. Linux is about choice :-) 

I am very pleased with Evince, though.

---

### Post by dobber1978 on 2011-04-03
Are there any tricks to installing Lubuntu?

I downloaded from both Torrents and their server and I can't get either to install.

What I tried:
Downloaded the .iso file for version 10.10 of Lubuntu and burnt it to a CD-R.
Changed boot sequence to CDROM first.
Disk in computer.
Powered up computer.
The Lubuntu screen comes up and I selected english as language
I ran the check disk and the disk checks out without error.
I next try to install Lubuntu.
I get the Lubuntu logo and that is where it hangs up.

Now I noticed that it nevers asks to format the hard drive. Do I have to do this on my own?

Thanks again,
Jeff

---

### Post by Dutch70 on 2011-04-04
Next time you boot up the disc, select "Try lubuntu" We can get a lot more info from there.

Just to let you know, I had a problem installing Lubuntu on one of my older computers, but Xubuntu installed without a hitch. At the same time, I've seen people try to install Xubuntu and have the same problem, while Lubuntu installed easily for them. Not quite sure of the difference yet.

---

### Post by mörgæs on 2011-04-04
If there is trouble installing Lubuntu, try post 261 here:

[http://ubuntuforums.org/showthread.php?t=1155961&page=27](http://ubuntuforums.org/showthread.php?t=1155961&page=27)

---

### Post by dobber1978 on 2011-04-05
Ok, ended up getting Lubuntu installed.

Ended up using the direction at the following address:
[https://wiki.ubuntu.com/Lubuntu/DocumentationHelp/MinimalInstall](https://wiki.ubuntu.com/Lubuntu/DocumentationHelp/MinimalInstall)

Installation worked like a charm.

Now does anyone have a wireless card that will work in this old machine that Lubuntu will recognize?

---

### Post by Joe of loath on 2011-04-06
what interfaces does it have? Mini pci, pcmcia etc?

---

### Post by dobber1978 on 2011-04-06
Sorry, it's the one that goes in the side and is eject-able. Believe this is the pcmcia.

---

