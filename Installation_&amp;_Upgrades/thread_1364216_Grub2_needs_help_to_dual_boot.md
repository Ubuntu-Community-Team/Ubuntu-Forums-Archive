---
title: "Grub2 needs help to dual boot"
date: 2009-12-25
forum: Installation &amp; Upgrades
---

### Post by rondackcpu on 2009-12-25
Sorry to beat this Grub2 thing to death, but I'm stuck.  My "test" machine is a dual boot system that, until today, had Jaunty and Karmic dual booted.  The Jaunty install was perfectly normal (with Grub Legacy as the loader).  Karmic was installed from an early Alpha (with Grub Legacy as the loader) and updated regularly to keep it current.  Grub Legacy worked perfectly to boot either Jaunty or Karmic, as desired.

Today, I decided to replace Jaunty with Lucid from one of the daily builds.  The "test" machine would then have Karmic and Lucid as the two operating systems.  The install went fine; Lucid installed Grub2 and replaced the MBR appropriately.  Update-grub and Os-prober were run a couple of times and Karmic was found -- but only the recovery mode entries were picked up by Grub2.  Selecting one of the Karmic entries in the Grub menu does indeed start Karmic in the recovery mode rather than the ordinary mode.  It's painful, as the recovery mode always is.  Lucid starts and runs beautifully when selected.

What should I do now?

I suppose I could reinstall Karmic, now with a copy using Grub2, but I would not learn anything about Grub2 by doing that.

Thanks for your help.

CRS

---

### Post by Herman on 2009-12-25
```
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    [COLOR=Red]**set quiet=1**[/COLOR]
    insmod ext2
    set root=(hd2,1)
    search --no-floppy --fs-uuid --set 6d6af125-7087-4fb6-afbc-14ddeeb465b8
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=6d6af125-7087-4fb6-afbc-14ddeeb465b8 ro   [COLOR=Red]**quiet splash**[/COLOR]
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic **[COLOR=Navy](recovery mode)[/COLOR]**" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd2,1)
    search --no-floppy --fs-uuid --set 6d6af125-7087-4fb6-afbc-14ddeeb465b8
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=6d6af125-7087-4fb6-afbc-14ddeeb465b8 ro [COLOR=Blue]**single**[/COLOR] 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
```Here's a snippet from one of my grub.cfg files showing both the normal boot entry and the recovery mode boot entry.
So we can easily see the differences, I have coloured them red or blue.

As you can see, the most important difference is in the kernel options, for the normal boot it just has 'quiet splash' for the kernel options, but the recovery mode has 'single' (single user mode), as a kernel option.

If you have Lucid running and you want to add a custom boot entry for Karmic, you might begin by using the cat command to bring up your current /boot/grub/grub.cfg,
```
cat /boot/grub/grub.cfg
```Select one of your Karmic boot entries with your mouse and copy and paste it to a text file.

Make the desired changes and save the file for the time being.

I'll be back in a while to help you make that into a custom boot entry which will boot your Karmic installation via the symlinks in /

I have to go for now, ....

---

### Post by Herman on 2009-12-25
alright, I'm back!

Okay, so you get the data you copied on your text file and you add the bits I have highlighted in red in the post above and you delete the parts I have highlighted in blue, and you should end up with something that looks like this, except it will have your own unique file system ID number in it and the relevant partition number to suit your installation,
```
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd2,1)
    search --no-floppy --fs-uuid --set 6d6af125-7087-4fb6-afbc-14ddeeb465b8
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=6d6af125-7087-4fb6-afbc-14ddeeb465b8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
```Next, you should delete the  word '/boot/' from the file paths to your Linux Kernel and initrd.img files, and also delete the numbers after the kernel and initrd.img that refer to the exact, specific kernel and initrd.img.
The reason for that is so we will be booting by the symlinks (shortcuts) to your kernel and initrd.img, which are located in / , and always point to your most up to date kernel and initrd.img files. That way you'll be automatically booting the most advanced kernel and initrd.img without needing to edit GRUB every time there's an update. 

Oh, and you can change your operating system's title to something a little more user freindly while we're at it, for example, 'Karmic Koala'.

You should end up with something that looks like this, but with your own file system UUID numbers, etc,
```
menuentry "Ubuntu Karmic Koala" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd2,1)
    search --no-floppy --fs-uuid --set 6d6af125-7087-4fb6-afbc-14ddeeb465b8
    linux   /vmlinuz root=UUID=6d6af125-7087-4fb6-afbc-14ddeeb465b8 ro   quiet splash
    initrd    /initrd.img
}
```

---

### Post by Herman on 2009-12-25
Next, we're going to turn your file into a script and copy it to your /etc/grub.d directory and rename it with an appropriate filename for it to be added to your grub.cfg.

Add this to the top of your file,
```
#! /bin/sh -e
echo "Adding custom boot entry(s)" >&2
 cat << EOF
```Add this to the bottom of your file,
```
EOF
```By now, your file should look something ike this,
```
#! /bin/sh -e
echo "Adding custom boot entry(s)" >&2
 cat << EOF
menuentry "Ubuntu Karmic Koala" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd2,1)
    search --no-floppy --fs-uuid --set 6d6af125-7087-4fb6-afbc-14ddeeb465b8
    linux   /vmlinuz root=UUID=6d6af125-7087-4fb6-afbc-14ddeeb465b8 ro   quiet splash
    initrd    /initrd.img
}
EOF
```Click on your file and re-name it '06_custom'.

Copy your 06_custom to your /etc/grub.d directory.
```
sudo cp 06_custom /etc/grub.d/
```Where: 06_custom is located in your /home/usernam directory, and not inside any other folders.

Change the file permissions on the file to make it executable,
```
sudo chmod 755 /etc/grub.d/06_custom
```Run grub-mkconfig to add it to your grub menu,
```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```That's it!
You should be able to reboot and choose Karmic Koala in normal mode from now on.

Actually, it wasn't all that complicated was it?, I just used a lot of steps to try to make sure I did a good job of explaining myself clearly, I hope it's all easy to follow.

---

### Post by rondackcpu on 2009-12-26
Thanks, Herman, for your reply and the effort you took to compose it.  As time allows I will follow the directions and hopefully mark the post "SOLVED".  

CRS

---

### Post by rondackcpu on 2009-12-26
Herman,

Are there a couple of "oop"s?

On the description of the file to chmod should it have been a / rather than a . between the opening parts and 06_custom?

Should there have been an update-grub somewhere?  Run with sudo or not?

Karmic and Lucid show up on the boot screen, but offer no boot locations.

CRS

---

### Post by Herman on 2009-12-26
> On the description of the file to chmod should it have been a / rather than a . between the opening parts and 06_custom?Oops! Yes, sorry, I fixed it, but yes, I did make a typo there! Well caught!
> Should there have been an update-grub somewhere?  Run with sudo or not?We can run update-grub or we can run grub-mkconfig, the two commands are quite similar because they both cause a new grub.cfg to be generated.
Most people are used to thinking of 'update-grub' because they remember the name of the command from GRUB Legacy, and most documentation still prescribes 'update-grub'.
 For while when I was experimenting with GRUB 2 I was getting feedback from the shell with a message something like 'update-grub is depricated, please use grub-mkconfig instead'. I have the impression the devs would like us to change our habits.
The grub-mkconfig command is newer, it wasn't available in Jaunty Jackalope or earlier, but has been available in Karmic Koala since sometime fairly early in Karmic's development. I prefer to use that one and encourage others to do the same. It's more versatile, with the -o option we can replace the normal file name and file path for our grub.cfg with anything we like. That could be useful if we're doing something special with GRUB.  :)

Sorry about the typo, I hope everything goes smoothly for you now that's fixed.

---

### Post by Herman on 2009-12-26
> Karmic and Lucid show up on the boot screen, but offer no boot locations.I'm not sure if I understand what you mean here. I guess you mean you have the titles in your GRUB menu but the boot stanzas after them are truncated in your grub.cfg?
If that's what you mean then I'd guess that the developers are in the middle of making some changes with Lucid's GRUB and maybe we should give it a rest for a while and revert to Karmic's GRUB until they're finished, and come back and try again later. 
What does you new grub.cgf look like? (Just the boot stanzas will do).

---

### Post by rondackcpu on 2009-12-26
Sorry, my bad.  When Grub2 presents the boot menu, the first two lines are just 

"Ubuntu Karmic Koala"
"Ubuntu Lucid Lynx"

without any mention of where or what was going to be booted.  I didn't try highlighting them as I thought they were defective.  But they do work.  There is still a bunch of other stuff on the Grub menu screen left over from other attempts at creating a grub.cfg file.  Will that go away eventually?

If this will keep both installs current as one or the other brings up a new kernel, this will be a great improvement over what I had been doing (manually editing the menu.lst of the governing install under Grub Legacy).

Thanks again for your help.

CRS

---

### Post by Herman on 2009-12-26
> If this will keep both installs current as one or the other brings up a new kernel, this will be a great improvement over what I had been doing (manually editing the menu.lst of the governing install under Grub Legacy).Yes.
Your Lucid Lynx installation owns the GRUB you're using, so it will keep updating it's own entry with every Lucid Lynx kernel update.

Normally, GRUB2 is able to automatically scan other operating systems and update the grub.cfg file to boot all your other operating systems by their most recent kernels too. 
Generally speaking, GRUB2 contains a lot of great improvements over GRUB Legacy. 
There shouldn't be any need to go and edit GRUB menus manually menus anymore.  I don't know why yours seems to have malfunctioned and failed to add your Karmic entry automatically. 

Your Karmic Koala boot entry is now set up as a custom boot entry for booting whichever kernel and intrd.img file is current via the symlinks in the root of your Karmic installation. Symlinks are like 'shortcuts', and those are updated with every new Karmic kernel update, unless something goes wrong, but it would be rare for anything to go wrong with that. By convention, most of the popular Linux distros install symlinks in / leading to their most up to date kernel and initrd.img files.  

So you won't need to manually edit your GRUB menu anymore, it will stay up to date by itself.
> There is still a bunch of other stuff on the Grub menu screen left over from other attempts at creating a grub.cfg file. Will that go away eventually?
I don't know, that depends on what it is and how it got there. If you added entries to other files in /etc/grub.d, such as 40_custom, they will be persistant until you remove them from 40_custom and re-run grub-mkconfig or update-grub.
If you're talking about old kernels, those will stay there too, unless you go and remove the older kernels with synaptic package manager.

---

