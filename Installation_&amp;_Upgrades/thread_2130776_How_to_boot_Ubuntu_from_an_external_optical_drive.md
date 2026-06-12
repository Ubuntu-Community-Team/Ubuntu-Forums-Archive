---
title: "How to boot Ubuntu from an external optical drive?"
date: 2013-03-30
forum: Installation &amp; Upgrades
---

### Post by JimS on 2013-03-30
...
In my thread "SUSU x501a - How to boot Ubuntu live usb stick"
I had already found a solution before I wrote the thread.
I needed Windoz to do it.  Bad solution IMHO.
But there is still the related question:
How to boot Ubuntu from an external optical drive connected to usb port?

I bought an ASUS x501a laptop in March 2013.
Windoz 8 was installed.
My ASUS has no optical drive.
But I do have a new Samsung usb external optical drive.
So far I haven't been able to boot from the Samsung.
I haven't been able to see it in the bios.
Windoz does see the Samsung, but no go for booting.
Not even using the Windoz tricks I used to get
my usb stick to boot would get my Samsung to boot.

My ASUS has American Megatrends bios and Windoz 8.
I don't want/need Windoz 8 or do I?
I would like to get rid of Win8, 
but I'm afraid this laptop won't run with only Linux.
The bios seems too limited.
Some of its features seem hidden and I don't know how to unhid them.

Do I need Win8 just to be able to get this laptop to work?
I want Linux and only Linux and
I want to be able to boot both a usb stick
and a usb optical drive from my usb port
preferredly without Windoz installed.

Bottom Line:
How to boot Ubuntu from an external optical drive?
And can I do it without Windoz installed?

Suggestions  --  Opinions
...

---

### Post by darkod on 2013-03-30
The ext optical drives are the same as internal cd-rom. If you select to boot from cd-rom, it should. With win8 preinstalled you probably have Secure Boot enabled in bios, you might need to disable it first.

Other than that, it should boot fine. This has nothing to do with ubuntu, it's a hardware issue with your machine.

It should boot from cd or usb just fine, as long as they are prepared correctly (bootable).

---

### Post by JimS on 2013-03-30
...
Thanks darkod.

But no love here.

With my Samsung external optical drive connected
and without going into Windoz, I went straight into bios.
Here is what I got:

I didn't have to change anything.
I/O Interface Security Secure Boot state was Disabled.
Secure Boot Control was Disabled.
USB Interface Security, USB Interface was Unlocked.

Boot Option Priorities show only Boot Option #1
which is Windows Boot Manager (PO: Toshiba ....
There is an option: Disabled.  I didn't touch that.
No Boot Option #2.   No cd-rom option.  No usb-hdd option.

There is a Add New Boot Option where I can supply
a name for the option, a filesystem, and its path.
Don't know how to do this.  Maybe this could
do the trick so that I could dump Windoz and
gain better control of my ASUS laptop.

If Windoz can turn on the usb port so I can boot a usb stick,
then Linux should be able to do the same, IMHO.
Also it would seem logical that if this PC had an optical drive installed,
then the bios would show that option.
But where there is no drive installed physically,
the option may still be available, even if hidden.
Again IMHO.

I want a Linux solution, not a Windoz solution.

I'm thinking this Laptop is too limited to be
a useful Linux only PC.  I may return it.

Suggestions  --  Opinions
...

---

### Post by darkod on 2013-03-30
What if you try to go into the one time boot menu of the board, without going into bios? It depends on the board, but usually you call the boot menu with F12 right after POST ends.

Is there cd-rom entry you can use there?

Go through the manual for the laptop, look at the boot options and how to boot from cd.

---

### Post by JimS on 2013-03-31
...
darkod - thanks for the idea.  

Oldfred also mentioned the following in another post:
UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/...ows-to-go.aspx](http://social.technet.microsoft.com/...ows-to-go.aspx)

I replied:
For my ASUS there is a bios utility key but no Boot Menu key.

darkod - BTW F12 did not work.  There seems to be no Boot Menu key.
I wonder why the above mentioned Microsoft page did not have it.
Many of the other PCs mentioned had Boot Menu keys.

Since this laptop has no optical drive, the manual makes no mention of one.
I find no mention in the bios either.
My ASUS sees my external usb optical drive, but won't boot from it.
Even using the windoz 8 trick which allowed me to boot from a usb stick,
did not also allow me to boot from the same port with my external optical drive.

Does Linux have a trick where I can trick my PC to think it has an internal optical drive,
and that the internal opitical drive can be a boot drive.
Then I think the bios will accept my external optical drive as a boot drive.

I have a desktop PC which I built and it has an AMI bios also.
Maybe I'll remove its optical drive and see how the bios responses.
I bet its boot entry disappears.

It is early morning and past time for this septuagenarian to go to bed.
Good night.
...

---

### Post by darkod on 2013-03-31
I don't understand what you mean by those "tricks" you keep mentioning. When we talk about booting, the process starts before any OS is loaded, the boot process actually loads the OS. So, no sense of talking about any windows or linux tricks.

If your machine can't boot from the ext cd-rom to start loading the ubuntu cd, you are not even inside linux to use any tricks, right?

On my home server I also don't have a cd-rom installed and I used ext cd-rom to install ubuntu server, and it worked great. The computer has to be able to boot from ext cd-rom. If it can't, it's rubbish. I have even booted older servers with ext cd-rom.

It sounds to me like the computer has very limited capabilities. No Boot Menu, no boot from ext cd-rom, etc...

---

### Post by The Cog on 2013-03-31
What you could do is remove the drive from the laptop and put it in a different machine, perform the install, then put it back again.

My netbook uses F11 rather than F12 for the one-time boot menu. The prompt appears at the same time as press DEL for BIOS setup.

---

### Post by dabl on 2013-03-31
According to the manual, there is a "Boot" tab in your BIOS, and it looks like you will need to do one of these:

- enable the "Launch PXE OpROM"

That may be sufficient.  If not, then

- go to the "Add / Delete" boot options, and add the USB device (when it is connected and powered up).

---

### Post by JimS on 2013-03-31
...
darkod
Tricks: The trick I'm writing about is the ability
of win8 to add a boot option (usb-stick) to the bios.
Can Ubuntu add a boot option to the bios
such as usb-stick and/or usb external optical drive?

I have a desktop PC which has only Linux (Mint 13 xfce - no windoz)).
This desktop PC will not boot from usb-stick.  Does Ubuntu or Mint
have the same ability as win8 to allow booting from usb-stick?

Yes, I agree, this ASUS x501a does seem very limited.

The Cog
I will not remove the drive from my new ASUS laptop.

I can bring us the bios holding down F2 key.  There is no
prompt for Boot Menu.

dabi
Yes, there is a boot tab as I mentioned before.
It has only one option, the hdd.

All
Thanks to all for your suggestions.  They are much appreciated.
I'm not going to mark this solved, since there has been none.
I intend to return the laptop.

JimS  the Septuagenarian
...

---

### Post by sudodus on 2013-04-01
> Tricks: The trick I'm writing about is the ability
of win8 to add a boot option (usb-stick) to the bios.
Can Ubuntu add a boot option to the bios
such as usb-stick and/or usb external optical drive?

I have a desktop PC which has only Linux (Mint 13 xfce - no windoz)).
This desktop PC will not boot from usb-stick.  Does Ubuntu or Mint
have the same ability as win8 to allow booting from usb-stick?

Ubuntu cannot write to the bios. But from Ubuntu you can add boot options to the grub menu, for example using the file 
```
/etc/grub.d/40_custom
```
Mine looks like this
```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Boot UBUNTU 10+ BASED SYSTEM from [COLOR=#ff0000]/media/multimed-2/CD/candidate.iso[/COLOR]" {
 set [COLOR=#ff0000]isofile[/COLOR]="[COLOR=#ff0000]/CD/candidate.iso[/COLOR]"
 set [COLOR=#ff0000]root[/COLOR]='(/dev/sd[COLOR=#ff0000]a[/COLOR],msdos[COLOR=#ff0000]2[/COLOR])'
 search --no-floppy --fs-uuid --set=[COLOR=#ff0000]root[/COLOR] [COLOR=#ff0000]d3f3f4a3-3d6e-4e4f-8e1a-c2f0de792f90[/COLOR]
 loopback loop ($root)$isofile
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
 initrd (loop)/casper/initrd.lz
}
menuentry "External drive (on /dev/sdb) if no eSATA drive in slot b. edit if necessary" {
        insmod part_msdos
        insmod fat
        set root='(hd1)'
        drivemap -s (hd0) ${root}
        chainloader +1
}
```
- The first entry boots from Ubuntu flavour iso files, that you can store on your internal HDD. You need to [COLOR=#ff0000]edit[/COLOR] the isofile and root id data to fit your situation.

- The second entry boots from a second drive, which can be a USB or an eSATA drive.

Finally, run ```
sudo update-grub
``` to make it active (copy it to /boot/grub/grub.cfg)

---

### Post by JimS on 2013-04-02
...
sudodus  --  Thanks for the reply.

I guess I'll have to study up on this kind of coding
and study up on grub.  Sounds interesting.
I don't much about it.
Where can I learn?
My coding knowledge was from the 1970's - 90's.
Mostly mainframes and very little of that.

JimS
This old dog can learn new tricks
...

---

### Post by sudodus on 2013-04-02
This link is a start

[[COLOR=#ff0000]https://help.ubuntu.com/community/Grub2[/COLOR]]("https://help.ubuntu.com/community/Grub2")

and then you can browse the internet for tutorials about Grub2.

Good luck :-)

By the way, this is actually rather simple compared to old time programming ;-)

---

