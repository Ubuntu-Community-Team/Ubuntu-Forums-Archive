---
title: "Karmic 9.10 R.C.- Grub: Error: No Such Device"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Duncan J Murray on 2009-10-25
I recently tried a fresh install of Karmic Koala 9.10 RC on an IBM Thinkpad T40 1.3Ghz 1.25Gb 40GB laptop.

The installation went fine, but when I tried to boot the laptop it came up with this error:

Error: No Such Device #####################

where ## is the UUID (apparently)

Grub 2 loads up, and allows you to try starting from the installed kernal and safe mood, but both of these bring up the same error.

Has anyone else had this problem?  And did they find a work around?

It has already been reported as a bug here...
[https://bugs.launchpad.net/debian/+source/grub2/+bug/403408](https://bugs.launchpad.net/debian/+source/grub2/+bug/403408)

It's very annoying as was quite keen to install 9.10, but I've just had to reinstall 9.04 now.

All best,

Duncan.

---

### Post by 4listair on 2009-10-26
Yes, same experience on a Dell Latitute D505 (laptop), where the HDD was replaced from the original and has XP on the first partition, so Karmic was being installed on a different partition.

Grub recognises the XP install and will boot fine into that from the menu.

Karmic was installed form the RC Desktop ISO loaded as a bootable USB, built from 9.10 on a different machine. Installation was directly from the live boot menu and not from the live desktop. I have tried installing from Alternate and the outcome is the same.

---

### Post by 4listair on 2009-10-26
I have just finished a successful install on a different D505 (Lat2) which also have an XP primary partition. The only difference, immediately to mind, is that the XP on Lat2 is fully installed, whereas the XP on Lat1 is not, so is perhaps making use of a hidden partition also (like you mentioned in your update to the bug thread).

---

### Post by 4listair on 2009-10-26
Well I recovered D505 Lat1 by using an USB Alternate of 9.10 RC and starting a shell on the Ubuntu partition. Ran:
aptitude update
aptitude safe-upgrade
[then the suggestion from [https://bugs.launchpad.net/debian/+s...b2/+bug/403408](https://bugs.launchpad.net/debian/+s...b2/+bug/403408) (different line number)]

  if fs_uuid="`${grub_probe} --device ${device} --target=fs_uuid 2> /dev/null`" ; then
#    echo "search --no-floppy --fs-uuid --set ${fs_uuid}"
     echo ""
  fi

dpkg-reconfigure grub-pc
exit
[reboot]

---

### Post by Duncan J Murray on 2009-10-26
Hi Alistair,

can you explain to me what you did in a bit more detail?

After my failed install of 9.10, I ran the liveCD to see if I could also edit that line in the grub (I think 174) - by removing the stuff in the quotation marks.  However, I tried saving that, and running grub-update, but it didn't work.

It has just occurred to me now that I was attempting to edit the files on the CD, rather than on the harddrive.  I used terminal to get to /usr/lib/grub/grub-mkconfig_lib file - but would that have been the file on the CD rather than my install?

Also, how did you run aptitude update and aptitude safe-upgrade?  just typed it in terminal?

Thanks,

Duncan.

---

### Post by 4listair on 2009-10-26
Hi Duncan

Sure, I will try and explain a little more (BTW, there is a separate Karmic discussion forum inside the Development & Programming which is worth a look: [http://ubuntuforums.org/forumdisplay.php?f=359](http://ubuntuforums.org/forumdisplay.php?f=359) ).

For testing and repair of installations, I use both the Live "CD" (Desktop) and the Alternate. If you download the DVD ISO image, you get both versions in one package. The Desktop version offers installation and the Live environment; wheares the Alternate offers installation and a recovery/repair/rescue facilities. To follow my guide, you need this Alternate version (same variety, ie i386 or AMD64).

Booting from Alternate (CD/USB), the menu that comes up after selecting the language option is (BTW, prior to this, on some flaky systems, you may need to select "y" to graphic mode and hit return a few times):
Install Ubuntu
Check disk for defects
Test Memory
Boot from first hard disk
Rescue a broken system

In order to do the repairs I used below, I need to run these changes and updates on the actual HD partition where 9.10 RC is installed (that Grub can't get to). So I use the Alternate to 'skip' over this Grub fault and get me into a comman line shell, actively running on that partition. I select the following:

Rescue a broken system
[This runs an environment identical to a command-line install]
Select language
Setect country
Select keyboard
Enter PC name
Selct the partition that contains the failed 9.10 RC [/dev/sda6 for me]
Execute a shell in [/dev/sdXX]

With the correct selection of partition, this puts you in the / (root) directory, logged in as root ("#" prompt). A subset of the usual command line commands are available to confirm you are in the right partition (ls -l /home)  If you select the wrong partition, type exit and you can go back to the menu to re-select.

Then you can follow my earlier steps:
-----------
aptitude update
aptitude safe-upgrade
[then the suggestion from [https://bugs.launchpad.net/debian/+s...b2/+bug/403408](https://bugs.launchpad.net/debian/+s...b2/+bug/403408) (different line number)]

if fs_uuid="`${grub_probe} --device ${device} --target=fs_uuid 2> /dev/null`" ; then
# echo "search --no-floppy --fs-uuid --set ${fs_uuid}"
echo ""
fi

dpkg-reconfigure grub-pc
exit
[ reboot ] 
----------

During the 'safe-upgrade' errors may be encountered, as we are not in a normal full boot, where a few other things are mounted, but should not cause problems. A confirmation window may come up for version control, if so, select the package maintainer's version. The upgdate may appear to repeat itself but just let it run. It will finish back at the "#" prompt.

Note that I did both the update and edited the /usr/lib/grub/grub-mkconfig_lib so I don't actually know which of those two fixed my problem ;-)

If you are nervous with vi, save a copy of the file:

cp /usr/lib/grub/grub-mkconfig_lib  /usr/lib/grub/grub-mkconfig_lib.bac


To edit the file, use vi:

vi /usr/lib/grub/grub-mkconfig_lib

[go to line 174]

:174

[make the edits, as above]
[to begin editing under the cursor, type: i]
[to quit editing, press Esc]
[to begin editing after the cursor, type: a]
[if you make a mistake, press Esc, then u (multiple times, if required)]
[to exit vi without saving: Esc, :q!]
[note that vi commands are case sensitive]
[finish editing, save and exit vi:]

Esc
:x


Now run:
dpkg-reconfigure grub-pc
exit
[reboot]

---

### Post by Duncan J Murray on 2009-10-27
IT WORKS!!!!

My laptop is saved...

The aptitude bit threw up a load of errors, but I managed to use vi (with your helpful abbreviated guide) without destroy the file with my clumsy key presses.

Cheers!

Duncan.

---

