---
title: "Checking md5sum of install cd"
date: 2005-10-17
forum: Installation &amp; Upgrades
---

### Post by geofff on 2005-10-17
How do I check the md5sum of a burned install cd? I am doing a full reinstall of Breezy as so many things seem to be running badly but I want to make sure that what I'm loading has no faults. 

I've downloaded the iso file from mirror and checked its md5sum against the sum given by the mirror (by command in terminal "md5sum <full address of .iso file>". It could perhaps have been more elegant but it worked!

I've burned the cd by opening the file containing the .iso file, right clicking, and clicking "write to disc". As this doesn't give the option to change the write speed (option is greyed out) I have gone into "Applications>System Tools>Configuration Editor>apps>nautilus-cd-burner and changed the default speed to 2  (I want to be quite certain I'm getting a clean copy!) and checked the burnproof and overburn options. I've clicked enter before exitting which is the only way I can think of to save the changes. (A "Save Changes" option would have been clearer)

I've then clicked "write to disc" on the original burn window. 

After burning I've returned to the nautilus-cd-burner section. burnproof and overburn are still checked but the default speed shows as 0! I don't know what speed it has been burned at. 

This wouldn't be so bad if I could check the md5sum was OK. However I have tried "md5sum /dev/cdrom" in terminal and get "Input/output error". As far as I know this is the right command? Is there another?

Does this result mean the cd is corrupt? I've read other posts etc that seem ambivalent on this, in particular "The fact that
md5sum is not able to read the raw disc does not mean that it is corrupt" by Matt Zimmerman [https://bugzilla.ubuntu.com/show_bug.cgi?id=2751](https://bugzilla.ubuntu.com/show_bug.cgi?id=2751). So how do you check the md5sum of a cd? (Sorry if the rest of that bug thread had an answer but much of it I didn't understand)

So if I don't know what speed I'm burning at, and whether the md5sum is right or not, how do I know what I'm loading onto my machine?

Should the command "md5sum /dev/cdrom" come up with a checkable sum? How can I burn a bootable file at a speed I can control. 

Enlightenment please!

---

### Post by geofff on 2005-10-17
I've just gone back into nautilus-cd-burner and it seems there are two ways to change the burn speed 1. by clicking on the value which enables the number to be changed directly after which the only way to save is by pressing return (and it looks as though this may not happen) or 2. by double clicking on the i icon which brings up an "edit key" window. To close this window you have to click OK which presumably saves the change. I think I did #1. Is this a bug?

I'll now go back and burn another cd and see if I can get an md5sum check on that.
I'll post the result.

---

### Post by geofff on 2005-10-17
Hope dashed!

On trying md5sum /dev/cdrom on the new cd I again get "input/output error" and on checking nautilus-cd-burner the speed has reset to 0!

I now do need help!

---

### Post by stuporglue on 2005-10-17
Try checking the md5 of /dev/cdrom with sudo 

sudo md5sum /dev/cdrom

Normal users can't access devices directly. 

Although selecting a slower speed for burning won't do anything detrimental, you should be safe using the detected speeds. That's why CDs and CD burners are rated for certain speeds -- so we don't have to think about it (as much). The only caveat is if you don't have enough buffer, in which case burning slower, or doing less with the computer during the burn, would help.

---

### Post by john_c on 2005-10-17
Geoff:

Some time ago I was having major difficulty in getting accurately burned cd's.  Turned out to be a heat problem with the cpu but anyway I ended up finding out how to obtain an accurate md5sum for the cd itself.  The below method has always worked and I have burned quite a few .iso's.  

I use a short script that I found quite a while ago on the net under "coasterless cd burning".   I believe the website for "coasterless" is [www.troubleshooters.com/linux/coasterless.htm](www.troubleshooters.com/linux/coasterless.htm) but for some reason it isn't available as I write this.

The script is called rawread.sh and the contents are as follows:


#!/bin/sh
device=$1

blocksize=`isoinfo -d -i $device | grep "^Logical block size is:" | cut -d " " -f 5`
if test "$blocksize" = ""; then
	echo catdevice FATAL ERROR: Blank blocksize >&2
	exit
fi

blockcount=`isoinfo -d -i $device | grep "^Volume size is:" | cut -d " " -f 4`
if test "$blockcount" = ""; then
	echo catdevice FATAL ERROR: Blank blockcount >&2
	exit
fi

command="dd if=$device bs=$blocksize count=$blockcount conv=notrunc,noerror"
echo "$command" >&2

$command



End of script

In order to use this, the following command is given (with the burned cd in the drive (/dev/hdc):

./rawread.sh /dev/hdc | md5sum

(cd to the directory that the rawread.sh file is in before giving the command).

I always use cdrecord on the command line to burn iso's.  I find it easy to control the speed and other features.  This information was also on the "coasterless" site.  The command I use is:

cdrecord dev=/dev/hdc speed=4 padsize=63s -pad -v -eject isofile.iso

Hope this is of some help.

John

---

### Post by geofff on 2005-10-17
Stuporglue  thanks for that. I tried sudo and still get the same Input/output error.

john_c this sounds as though it will help. All I need to do is find out what writing scripts is about! No time now but will come back to this.

Thanks Geofff

---

### Post by john_c on 2005-10-17
Geoff:

To use the rawread.sh script do the following:

- open gedit.
- copy and paste the rawread.sh contents given in my last post into the gedit document.  Copy everything from "#!/bin/sh" down to and including "$command".
- save the document as rawread.sh           (as unicode (Utf-8))
- change the permissions of rawread.sh to rwxr--r-- with "chmod 744 rawread.sh"     (no quotes).

You will now be able to use it in the command line as noted earlier 

"./rawread.sh /dev/hdc |md5sum"    (no quotes)

My computers use /dev/hdc as the device name - change this if it isn't the case for yours.

I have used this on mounted and unmounted cd's and obtained the same md5sum result.

Good luck,

John_c

---

### Post by john_c on 2005-10-17
Geoff:

One further comment.  I can get an md5sum check of a cd by using "md5sum /dev/hdc" but it will always be different from doing the md5sum with the rawread.sh script and it will be different from the published md5sum of the .iso file even if it has been downloaded and burned accurately.

My understanding is that the "md5sum /dev/hdc" reads past the end of the files burned to the cd and this of course gives a different md5sum.  The rawread.sh script finds the exact end of the data burned to the cd and thus the md5sum it creates is accurate.

John_c

---

