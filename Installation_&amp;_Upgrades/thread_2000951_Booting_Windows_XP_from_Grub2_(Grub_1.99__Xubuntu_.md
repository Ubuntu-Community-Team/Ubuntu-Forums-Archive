---
title: "Booting Windows XP from Grub2 (Grub 1.99 / Xubuntu 12.04)"
date: 2012-06-10
forum: Installation &amp; Upgrades
---

### Post by nowaibro1 on 2012-06-10
Hi guys,

I'm not sure what else to do, and have tried all I can so now I'm asking for help.

Here's my problem: Basically, I have two hard drives. On one is Windows XP (Ch 2 Master/sda), on the other I have setup Xubuntu 12.04 (Ch3 Master, sdb).

My windows MBR is fine. I can boot my Windows partition by selecting that HD from the BIOS. Likewise the MBR on the other hard drive is fine and I can boot Xubuntu from grub. What I would like to do is to be able to chainload ntldr (I believe that's the right terminology) from grub.

os-prober does not detect Windows - unless the partition is mounted but it can't write anything anyway because it says it needs to be run as root. However sudo os-prober doesn't seem to do anything at all, so that doesn't help either.

```
ERROR: you must be root
ERROR: you must be root
/usr/lib/os-probes/mounted/20microsoft: 47: /usr/lib/os-probes/mounted/20microsoft: cannot create /var/lib/os-prober/labels: Permission denied
/dev/sda1:Microsoft Windows XP Home Edition:Windows:chain
mkdir: cannot create directory `/var/lib/os-prober/mount': Permission denied

```I've tried many different ways of trying to boot my Windows install from grub by editing an appropriate file in grub.d (yes it's executable and it does get written to grub.cfg like it should) but no cigar. The best I've gotten is a few different errors from grub, or repeated restarting of grub.

As far as I can tell, I want to boot Windows from hd0,1 but no luck. I've tried drivemap -s, accessing it by uuid etc. Just for reference, I've tried the Ubuntu grub2 guide, reading the grub 1.99 manual, the archlinux grub2 guide, the fedora grub2 guide, the dedoimedo grub2 tutorial and various ideas from forum posts I've found.

It may well be an idea to go back to square one and start again. If there's any info you need that could help, just ask, although I don't have a whole lot of experience with Linux.

Here is the bootinfo output: [http://paste.ubuntu.com/1033791/](http://paste.ubuntu.com/1033791/)

Thanks in advance.

PS. I'm fairly tired as it's now quite late here, but I'll be on again tomorrow to see if anyone's got some ideas. Cheers.

---

### Post by sudodus on 2012-06-10
Hi!

Try what happens if you do the following:

- boot Xubuntu

- open a terminal window

- run the following command
```
sudo update-grub
```
(You should notice if Windows is recognized)

- reboot (you should have an option to boot Windows)

Good luck!

---

### Post by nowaibro1 on 2012-06-10
Hey, thanks for the help.

Sorry, I should've made that more clear. Update-grub doesn't detect my windows installation at all.

```
myddraal@Skippy-Xubuntu:~$ sudo update-grub
[sudo] password for myddraal: 
Generating grub.cfg ...
Adding Windows XP to GRUB 2 menu ## NOTE: This is from my script (/etc/grub.d/09_windaz), which doesn't work.
Found linux image: /boot/vmlinuz-3.2.0-24-generic
Found initrd image: /boot/initrd.img-3.2.0-24-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
Found memtest86+ image: /memtest86+.bin
done
myddraal@Skippy-Xubuntu:~$ 

```Running os-prober won't either *unless* sda1 is mounted, but I don't seem to be able to run os-prober as root (I'm not sure why?) so it can't add Windows to the grub menu even though it seems to have some luck in finding it.

Cheers

---

### Post by drs305 on 2012-06-10
Add the following to the lines below those already in /etc/grub.d/40_custom:

> menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" --class windows --class os {
        insmod part_msdos
        insmod ntfs
        set root='(hd0,msdos1)'
        search --no-floppy --fs-uuid --set=root 5E1C40441C401983
        drivemap -s (hd0) ${root}
        chainloader +1
}

Save the file and update-grub.

For whatever reason, your os-prober doesn't seem to be working. /etc/grub.d/30_os-prober is running, as it generates an (empty) section in grub.cfg. When testing it, I'm assuming you are trying "sudo os-prober" ?

Adding the above should work, but my disclaimer is that I don't run Windows.

You could try reinstalling os-prober with the following:
```
sudo apt-get install --reinstall os-prober
```

---

### Post by nowaibro1 on 2012-06-11
Awesome, thank your drs305 - It works!

Turns out after all that, I just needed to learn a bit about bash  scripting (specifically 'cat') and escape the '$' character in '$root'. Don't I feel a bit stupid :oops:.

I'd tried more or less that same script before, but I'd only been editing 09_windaz. It worked in 40_custom, but when I tried to copy it to 09_windaz it didn't. After comparing what was output to grub.cfg, turns out it was reading $root as (an empty) variable and thus not printing anything there, leaving a half written command.

For someone else's future reference, my windows config  now looks like this:
```
#!/bin/sh -e
echo "Adding Windows XP to GRUB 2 menu (09_windaz)" >&2
cat << EOF
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" --class windows --class os {
insmod part_msdos
insmod ntfs
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 5E1C40441C401983
drivemap -s (hd0) \${root}
chainloader +1
} 
EOF

```And after running update-grub is printed to grub.cfg like this:
```
### BEGIN /etc/grub.d/09_windaz ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" --class windows --class os {
insmod part_msdos
insmod ntfs
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 5E1C40441C401983
drivemap -s (hd0) ${root}
chainloader +1
} 
### END /etc/grub.d/09_windaz ###
```I reinstalled os-prober but it made no difference, not that it really matters to me now grub is configured how I want it. 
However, in case anyone is curious, here's how it's behaving: [http://paste.ubuntu.com/1034893/](http://paste.ubuntu.com/1034893/) (note the sudo os-prober at the end). If anyone wants to try and figure it out send me a PM or post here, I'll keep checking for the next few days.

Edit: Thank you to everyone who takes time to help out Linux newbs like myself, I'm sure it's not particularly rewarding, but it certainly doesn't go unappreciated.

---

### Post by drs305 on 2012-06-11
nowaibro1,

Glad you sorted it out.

As far as the failure of os-prober, it must be run as root (sudo os-prober). In the output you posted you did try that at the very end.

Disclaimer on what follows: I have never used RAID/LVM ...

Looking at your terminal output, when run as root, os-prober did not generate any error messages. I took a look at the content of os-prober and saw that there were several comments which would exclude drives/partitions, such as:
> 	# Exclude partitions that have whole_disk sysfs attribute set.
	if [ -d /sys/block ]; then
		# Exclude partitions on physical disks that are part of a
		# Serial ATA RAID disk.

There was also a section on LVM.

So that led to the next thought. Did you ever use RAID or LVM? Perhaps some remants are still hanging around which are telling os-prober to skip them. I have never used either, but I know that in the past some users had problems with setting up Grub and clearning up past RAID information helped. Perhaps this is your issue as well.

```

dmraid -an 	# activate RAID no
dmraid -si	# sets RAID inactive
dmraid -E -r  	# Erase metadata from RAID devices

```
or
```

sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
sudo apt-get remove dmraid

```
Note: If you once had RAID but no longer use it you may need to install dmraid first.  Also you can check your BIOS settings to make sure no RAID settings are activated.

---

### Post by nowaibro1 on 2012-06-12
Yep, that was the problem:
```

myddraal@Skippy-Xubuntu:~$ sudo dmraid --raid_devices -v
INFO: RAID device discovered:

/dev/sda: pdc, "pdc_ibahcbfd", stripe, ok, 390718720 sectors, data@ 0
myddraal@Skippy-Xubuntu:~$ sudo dmraid -E -r /dev/sda
Do you really want to erase "pdc" ondisk metadata on /dev/sda ? [y/n] :y
myddraal@Skippy-Xubuntu:~$ sudo os-prober
/dev/sda1:Microsoft Windows XP Home Edition:Windows:chain
myddraal@Skippy-Xubuntu:~$ 
```I've never actually setup a RAID, but I was using an older computer with some fairly early SATA/RAID controllers until the GPU died and I had to move my HD to my current tower.

It took a fair bit of mucking around to get SATA drives to work on it at all, especially without a PATA hard drive to boot from so I suppose it's not surprising I did this at some point (In fact I have a feeling it might have even been necessary to do it to install Windows, I can't quite remember as it was a year or two ago).

Just out of curiosity, do you know where dmraid saves the .dat files it supposedly generates? I did a bit of a search but couldn't find it.

Thanks again for the help, at least I've learned something out of all of this. ;)

---

### Post by drs305 on 2012-06-12
> **nowaibro1 said:**
> Yep, that was the problem:
Just out of curiosity, do you know where dmraid saves the .dat files it supposedly generates? I did a bit of a search but couldn't find it.

Thanks again for the help, at least I've learned something out of all of this. ;)

I hadn't seen this particular failure of os-prober before, so I learned something as well. Glad you have it all sorted out.

I have no experience with RAID but perhaps someone currently using it would let us know where the .dat files reside.

Happy Ubuntu-ing.  :-)

---

