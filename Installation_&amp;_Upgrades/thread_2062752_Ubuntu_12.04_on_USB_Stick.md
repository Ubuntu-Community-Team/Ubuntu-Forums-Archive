---
title: "Ubuntu 12.04 on USB Stick"
date: 2012-09-25
forum: Installation &amp; Upgrades
---

### Post by rich1939 on 2012-09-25
I installed Ubuntu 12.04 Desktop on a 32Gb stick on my Windows 7 computer. I wanted Ubuntu to be completely separate from my Windows hard drive's contents. It installed fine and is running as I'm typing this note.

I have a number of issues with it, however:

1) I was not given the opportunity to assign a root password, so how do I do that, now that it's running?

2) I don't really like the new interface and would prefer to use the "classic" one, with which I was familiar.

3) Finally, I downloaded and installed suggested updates, and found that my cursor was stuck and I was unable to unstick it. I had to re-install Ubuntu to write this note.

Please help with one or all of the above problems.

Thank you.

Rich Parker

---

### Post by cortman on 2012-09-25
> **rich1939 said:**
> I installed Ubuntu 12.04 Desktop on a 32Gb stick on my Windows 7 computer. I wanted Ubuntu to be completely separate from my Windows hard drive's contents. It installed fine and is running as I'm typing this note.

I have a number of issues with it, however:

1) I was not given the opportunity to assign a root password, so how do I do that, now that it's running?

2) I don't really like the new interface and would prefer to use the "classic" one, with which I was familiar.

3) Finally, I downloaded and installed suggested updates, and found that my cursor was stuck and I was unable to unstick it. I had to re-install Ubuntu to write this note.

Please help with one or all of the above problems.

Thank you.

Rich Parker


Hi- in answer to your questions-
1. Root is disabled by default in Ubuntu, it uses sudo instead. You can enable the root account by running

```
sudo passwd root
```

2. You can install gnome fallback-

```
sudo apt-get install gnome-panel
```

Then choose the Gnome Classic session at the login screen.

3. Not sure what caused this, but if your reinstallation is working fine, I wouldn't worry about it.

---

### Post by rich1939 on 2012-09-25
Thanks for the response.

Regarding my number 3) question, if I am not able to install updates, won't that be a problem? I like to keep my distributions up to date.

Thanks again.

Rich Parker

---

### Post by oldfred on 2012-09-25
How did you install to the flash drive.

The usual way to install is just the Ubuntu installer with possibly persistence to save some data. But that is for smaller flash drives 4GB or less and primarily as a way to create an installer rather than using a CD or DVD.

Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

But with a 32GB flash you have plenty of room for a full install, just like on a hard drive. USB flash will be a bit slower as USB port is slower than SATA port and flash is slower than hard drive especially for writes. But you can minimize writes and it is very functional. I have a full install of Ubuntu on a 8GB partition for testing in my 16GB flash with the remaining 8GB for data.

With grub2 persistent C.S.Cameron 12.04
[http://ubuntuforums.org/showthread.php?t=2042965](http://ubuntuforums.org/showthread.php?t=2042965)

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory Installation using alternative text based installer
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)
[http://ubuntuforums.org/showthread.php?t=1404664](http://ubuntuforums.org/showthread.php?t=1404664)

---

