---
title: "Grub2 Loop menu entry?"
date: 2009-10-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ranch hand on 2009-10-05
I am getting bored with grub2.  I have the bugger set up and running just great.

This will not do.

I can get step by step directions on making a loop entry for things I have no interest in booting.  I want to boot a LiveCD of an OS, probably 9.04 or 9.10 but I have a current Mandriva as well.

What the heck is, or how do you figure out, the boot path for these buggers?

---

### Post by VMC on 2009-10-05
> **ranch hand said:**
> I am getting bored with grub2.  I have the bugger set up and running just great.

This will not do.

I can get step by step directions on making a loop entry for things I have no interest in booting.  I want to boot a LiveCD of an OS, probably 9.04 or 9.10 but I have a current Mandriva as well.

What the heck is, or how do you figure out, the boot path for these buggers?

If your referring to the loop-back method, here's one of mine for PartedMagic:

```
menuentry "loop-back-pmagic from harddisk (findiso = pmagic-4.6.iso)" {
  loopback loop (hd0,5)/pmagic-4.6.iso
  gfxpayload=1024x768
  linux (loop)/pmagic/bzImage findiso=/pmagic-4.6.iso root=/dev/ram0 intel-2.4.1 noeject noprompt sleep=0 load_ramdisk=1 prompt_ramdisk=0 loglevel=0 keymap=us
  initrd (loop)/pmagic/initramfs
boot
}
```

The problem can be in the way initmfs gets installed. Lubuntu won't work and I can find no web page or anyone to contact regarding the issue.

Go [here]("http://gparted-forum.surf4.info/viewtopic.php?id=13623") for a convoluted explanation of what I'm referring to with a gparted livecd.

 Although, I think Ubuntu livecd's will work.

---

### Post by ranch hand on 2009-10-05
> **VMC said:**
> If your referring to the loop-back method, here's one of mine for PartedMagic:

```
menuentry "loop-back-pmagic from harddisk (findiso = pmagic-4.6.iso)" {
  loopback loop (hd0,5)/pmagic-4.6.iso
  gfxpayload=1024x768
  linux (loop)/pmagic/bzImage findiso=/pmagic-4.6.iso root=/dev/ram0 intel-2.4.1 noeject noprompt sleep=0 load_ramdisk=1 prompt_ramdisk=0 loglevel=0 keymap=us
  initrd (loop)/pmagic/initramfs
boot
}
```The problem can be in the way initmfs gets installed. Lubuntu won't work and I can find no web page or anyone to contact regarding the issue.

Go [here]("http://gparted-forum.surf4.info/viewtopic.php?id=13623") for a convoluted explanation of what I'm referring to with a gparted livecd.

 Although, I think Ubuntu livecd's will work.
I read somewhere about a problem with Ubuntu Live CDs so that may be the problem that I had the one time I tried it a while back.

I also tried the "generic" type menu entry then too and it didn't work either.  Works great now, I have changed all my custom entries to it and don't have to update them.  I even formated and installed a different 9.10 on one partition and, sure enough, didn't have to change the entry except to change the name between the ""s.

I really want to boot a Live CD but do not know how to find the right boot path in the image.  I will read the link you sent and see if that helps.

If this becomes something that works, grub2 will be the standard by which all boot loaders are judged by.

I don't know if you can tell but I am getting to like grub2 a lot.

---

### Post by ranch hand on 2009-10-05
What on earth is the;
```

gfxpayload=1024x768

```
for?

---

### Post by ayates on 2009-10-05
I had this working a while back and one day it just quit. After reading around someone suggested
doing a "ls" command from the grub command line. Sure enough, my hard drive designations wern't what I thought they were. Some update changed them. hd0 had becone hd1 and vice versa. I don't know how anything worked. Anyway, changed the loopback entry and I was in business again.

---

### Post by VMC on 2009-10-06
> **ranch hand said:**
> What on earth is the;
```

gfxpayload=1024x768

```
for?

That's because "vga=773" is depreciated now.

---

### Post by ranch hand on 2009-10-06
> **ayates said:**
> I had this working a while back and one day it just quit. After reading around someone suggested
doing a "ls" command from the grub command line. Sure enough, my hard drive designations wern't what I thought they were. Some update changed them. hd0 had becone hd1 and vice versa. I don't know how anything worked. Anyway, changed the loopback entry and I was in business again.
What did you have this working with?  Ubuntu LiveCD?

Here is what I have in my 09_custom file;
```

echo "Adding karmic-desktop-amd64.iso"
cat <<EOF
menuentry "karmic-desktop-amd64.iso" {
       set root=(hdo,16)
       loopback loop (hd0,16)/boot/iso/karmic-desktop-amd64.iso
       linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/karmic-desktop-amd64.iso --
       initrd (loop)/casper/initrd.gz
}
EOF

echo "Adding 2karmic-desktop-amd64.iso"
cat <<EOF
menuentry "2karmic-desktop-amd64.iso" {
       set root=(hdo,16)
       loopback loop (hd0,16)/karmic-desktop-amd64.iso
       initrd (loop)/karmic/initrd
}
EOF

```
This is what it comes to in the grub.cfg file;
```

menuentry "KinkyStoner1.0 on sda6" {
        set root=(hd0,6)
        linux /vmlinuz root=/dev/sda6 so quiet splash
        initrd /initrd.img
}
Adding karmic-desktop-amd64.iso
menuentry "karmic-desktop-amd64.iso" {
       set root=(hdo,16)
       loopback loop (hd0,16)/boot/iso/karmic-desktop-amd64.iso
       linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/karmic-desktop-amd64.iso --
       initrd (loop)/casper/initrd.gz
}
Adding 2karmic-desktop-amd64.iso
menuentry "2karmic-desktop-amd64.iso" {
       set root=(hdo,16)
       loopback loop (hd0,16)/karmic-desktop-amd64.iso
       initrd (loop)/karmic/initrd
}
menuentry "Jaunty 9.04, kernel 2.6.28-14-generic (on /dev/sda8)" {
        set root=(hd0,8)
        linux (hd0,8)/boot/vmlinuz
        initrd (hd0,8)/boot/initrd.img
}

```
Note the "Adding 2karmic-desktop-amd64.iso" addition to the grub.cfg file that is not there with any of the other entries.

I also find the terminal output interesting when running update-grub;
```

ker@ker-desktop:~$ sudo update-grub
[sudo] password for ker: 
Generating grub.cfg ...
Found Debian background: kinkyfruit.png
Adding KinkyA1 on sda16
Adding DailyGrub on sda22
Adding KinkyA4 on sda20
Adding Kinky Stoner1.0 on sda10
Adding KinkyStoner1.0 on sda6
Adding Jaunty on sda8
Adding Stoner1.1 on sda18
Adding Mandriva2009-Gnome on sda12
Adding Mandriva2009-KDE on sda14
Found linux image: /boot/vmlinuz-2.6.31-11-generic
Found initrd image: /boot/initrd.img-2.6.31-11-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu karmic (development branch) (9.10) on /dev/sda10
Found Mandriva Linux 2009.0 (2009.0) on /dev/sda12
Found Mandriva Linux 2009.0 (2009.0) on /dev/sda14
Found Ubuntu 9.04 (9.04) on /dev/sda18
Found Ubuntu karmic (development branch) (9.10) on /dev/sda20
Found Ubuntu karmic (development branch) (9.10) on /dev/sda22
Found Ubuntu karmic (development branch) (9.10) on /dev/sda6
Found Ubuntu 9.04 (9.04) on /dev/sda8
done

```
Note the total lack of mention of either entry in the out put.

Now, to be fair, neither of these entries, both of which do show up on the screen menu, is any good.  All I get is "file not found  push any button to continue".

WTF?

I hope someone has more of a clue than I do because I haven't got one (sudo apt-get install clue   does not seem to work).

---

### Post by ranch hand on 2009-10-06
All right, so if you enter things right like this;
```

echo "Adding karmic-desktop-amd64.iso" >&2

```
instead of
```

echo "Adding karmic-desktop-amd64.iso"

```
It shows up on the terminal output and correctly in the grub.cfg file and the screen menu.

Still doen't work.

---

