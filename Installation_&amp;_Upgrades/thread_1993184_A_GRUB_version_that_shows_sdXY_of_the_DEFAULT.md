---
title: "A GRUB version that shows sdXY of the DEFAULT?"
date: 2012-06-01
forum: Installation &amp; Upgrades
---

### Post by NTL2009 on 2012-06-01
In the GRUB menu, the default choices at the top do not show their sdXY locations, while the sdXY is shown for all the 'alternate' choices. I guess it is assumed that you know where the defaults are, but this isn't really the case when I'm playing with a bunch of installations on a couple different drives.

Maybe it is my imagination, but I could _swear_ that recently, while I was trying out different installations on external drives, that I saw the sdXY on the default choices. I thought that was great, a nice confirmation of just what I was loading. It might have been my MINT 12 install?

Anyhow, does anyone know if this is available, or some option somewhere to select. I guess the alternative is to go in and edit the menus manually.

-NTL2009

---

### Post by drs305 on 2012-06-01
The top menu items on a default Grub installation are always from the controlling GRUB. That will tell you if you happen to remember which is controlling and what partition it is on.

There are 3 ways I can think to do something to your liking. 

1. Edit the /etc/grub.d/10_linux script to include the partition number. I am about to leave on a business trip but I'll try to come up with the entry if I have time. Are you still using Maverick - it uses a different Grub than the current version?

2. Make a 06_custom menu. You wouldn't even have to put a real 
menuentry. You could just have the following (you wouldn't even need a command, I just like to include something in the menuentry itself):

> menuentry 'SDA1' {
	insmod ext2
}

Just copy 40_custom to 06_custom, add the above to each OS's /etc/grub.d folder, make it executable and run update-grub.

3. Make a simple background, include the partition name in the graphic somewhere, and add the .png, .tga or 8-bit jpeg file to /boot/grub. I like using different backgrounds for each OS so I can immediately tell the one controlling the boot.

---

### Post by drs305 on 2012-06-01
Here is a way to modify the 10_linux script. It's for GRUB 1.98, the default in Maverick.

I didn't find a section in 00_header or 10_linux which specifically identified the partition by device name, so I created a variable to extract the / partition (such as /dev/sda5).

In 10_linux:
Change:
> 
  linux_entry "${OS}" "${version}" false \
      "${GRUB_CMDLINE_LINUX} ${GRUB_CMDLINE_EXTRA} ${GRUB_CMDLINE_LINUX_DEFAULT}" \
      quiet

To:
> 
  **[COLOR="DarkRed"]mypartition=`mount | grep "on / type" | cut -d " " -f1`[/COLOR]**
  linux_entry "${OS}" "${version} **[COLOR="DarkRed"]on $mypartition[/COLOR]**" false \
      "${GRUB_CMDLINE_LINUX} ${GRUB_CMDLINE_EXTRA} ${GRUB_CMDLINE_LINUX_DEFAULT}" \
      quiet


The "mypartition" variable translates to "/dev/sdXY". You can modify the "cut" command to produce a different format.

---

