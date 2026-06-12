---
title: "Manually adding entries to Grub2"
date: 2009-09-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Bastanteroma on 2009-09-07
I'd like to try out [xPud]("http://www.xpud.org/") by pointing Grub at it, but the instructions are for legacy Grub, i.e. I'm supposed to add the following to my boot/grub/menu.lst:

title		xPUD 0.9
root		(hd0,0)
kernel	/xpud-0.9-image noisapnp lang=en quiet

How do I do the equivalent in Grub2?

---

### Post by drs305 on 2009-09-07
Bastanteroma,

Grub 2 significantly changed the way Grub entries are made. You don't just cut & paste the way you did in Grub Legacy. This makes the learning curve a little steep but the result is a much more flexible system.

You will probably want to make a 40_custom file, which is covered in both links. Just remember to run "update-grub" after you create or update any of the grub script files.

Here are two references to Grub 2 that you might take a look at:
[Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275")
[https://wiki.ubuntu.com/Grub2]("https://wiki.ubuntu.com/Grub2")

---

### Post by seamuso on 2009-09-07
Looking for similar help here too .. I had alpha4 installed and it created a file which had the correct code to boot my xp partition. I did a complete reinstall of alpha5 and that file wasn't created.

The problem lies in 30_os-prober enters my XP partition, the restore partition, and the utility partition that are on the drive. With alpha4, I believe the secondary file that was created was called 30_otheros (or something similar). This caused doupble entries in the grub menu, but I was able to comment out the sections I didn't want to see and set the 30_os-probe script as a non-executable and all of my double entries were fixed.

All of the searches I have done in trying to find an example snippet that will create the entry in grub.cfg only give the code AS found in grub.cfg, not as it should be scripted in /etc/grub.d .. Does anyone have that actual code that they could share which should also answer the original post in this thread 


thanks in advance .. at least I can get it to boot with pretty pictures though :lolflag:

---

### Post by drs305 on 2009-09-07
This is a 40_custom file that incorporates the **DEFAULT=saved** option in /etc/default/grub, which is why it looks rather complicated.

```

#! /bin/sh -e

prefix=/usr
exec_prefix=${prefix}
libdir=${exec_prefix}/lib
. ${libdir}/grub/grub-mkconfig_lib
echo "Adding Windows" >&2
cat << EOF
menuentry "Windows Vista" {
EOF
save_default_entry | sed -e "s/^/\t/"
cat << EOF
insmod ntfs
set root=([COLOR="DarkRed"]hd0,1[/COLOR])
search --no-floppy --fs-uuid --set [COLOR="DarkRed"]q67e48fd884ds522[/COLOR]
chainloader +1
}

```

Added Notes:
Make /etc/grub.d/40_custom executable.
Remove the executable bit from /etc/grub.d/30_os-prober to eliminate two possible Windows entries.
Run "sudo update-grub" after making any changes.

---

### Post by seamuso on 2009-09-07
Thanks, drs305!!

---

### Post by ranch hand on 2009-09-08
Using custom enteries is a smart thing to do, if only to back up your menu, as grub2 is updated in the repos regularly now.

If you want the custom entries at the top of your menu create a new file in /etc/grub/grub.d.  Copy your 40_custom file and rename the copy 06_custom.  It will appear between the 05_debian_theme and 10_linux files.  Run update-grub.

When you reboot your custom entries will be on the top of the menu where they are easiest to use.

I leave 30_os-prober active and let it do what it wants so that I can see what progress the repo updates are making.  All the silly stuff is below the menu I am using to boot with so it is not a problem if there are missing or duplicate entries.

---

### Post by seamuso on 2009-09-10
Booting XP on an EEEPC 1000HE

```

#! /bin/sh -e

prefix=/usr
exec_prefix=${prefix}
libdir=${exec_prefix}/lib
. ${libdir}/grub/grub-mkconfig_lib
echo "Adding Windows" >&2
cat << EOF
menuentry "Windows XP" {
EOF
save_default_entry | sed -e "s/^/\t/"

cat << EOF
       insmod ntfs
       set root=(hd0,1)
       search --no-floppy --fs-uuid --set a2f48f73f48f490d
       drivemap -s (hd0) \${root}
       chainloader +1
}

```

Was easy once I had the frsamework. Let 30_os-prober detect the available operating systems and save a copy of the grub.cfg for reference.

If you use the drivemap option and only put this -

${root} 

in the script, you won't boot the OS .. You must have the leading \

\${root}

for the script to work right when you run update-grub

You can also pull all of the correct uuid entries for the drives as needed from the grub.cfg.

Again, a HUGE thanks to drs305 for posting the script.

---

### Post by caryb on 2009-09-11
I seem to have the problem that after a kernel upgrade I have to manually add the new kernel to the grub.cfg file for it to pick it up, if I do a update-grub it still wont pick it up.


Cary

---

### Post by ranch hand on 2009-09-11
Build a custom file in /etc/grub.d.  Then the bugger will be there and you can edit it without it being over written in a file that is over written everytime you run update-grub.

We are getting grub2 updates and os-prober updates regularly.  The menu entries generated are changing.  This will come out right.

For now, and I think always for labeling, build a custom entry file.

---

### Post by edgar83 on 2009-10-19
So, what should I do to add the xPud voice on GRUB 2 bootloader? I didn't understand :(


Ciao!

---

