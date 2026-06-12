---
title: "Edgy Eft on Compaq Proliant Server"
date: 2006-11-03
forum: Installation &amp; Upgrades
---

### Post by scubanator87 on 2006-11-03
I was having the same problem here at work. Tried Several different install settings and mess with the smartstart cd 

for hours and couldn't figure it out. i finally found this post and adjusted it for my Edgy install. 

Here is what i did:

Go through your install normally.

when finished installing, boot from Install cd and chose Repair.

Go through the same start of the set up till error. 

after error a list of options will be available, scroll down and select "Start a Shell"

Make a folder to mount your install
$ mkdir /target

Now mount it for access (my partition defaulted to c0d0p1)
$ mount /dev/ida/<your partition goes here> 

now chroot
$ chroot /target

Now us vi/vim to edit the modules file to have the array boot on start. first make a back up!
$ cp ./etc/initframsfs-tools/modules ./etc/initframsfs-tools/modules_backup
$ vi ./etc/initframsfs-tools/modules

Once in vi, unless you have the commands memorized, you'll need a cheat sheet like me. i had to print it out to keep 

from running back to my desk over and over.how ever, you'll only need a few commands and i can help with that.

after you open its in command mode so do the following
hit j till your at the bottom of the document. 
hit o to open a new line after the current. 
type "cpqarray" and hit enter. this is the module for raid array
hit ZZ to save and exit

If your read the comments in the modules file, you notice that to update the list you need to run update-initramfs 

to update the init file. you need to run the -u option to update the list. 
$ update-initramfs -u 

Now all you have to do is reboot! yay your system now works. :-)

Remember: This is what i did to make it work for me and suggestions on how to improve this method are welcome :-)

---

### Post by gnux071 on 2006-12-14
Was this for the server or desktop distro?

---

### Post by scubanator87 on 2006-12-15
This is for the server install how ever, some one else has posed a easier/cleaner method. 


[http://www.ubuntuforums.org/showthread.php?t=255335&page=2&highlight=compaq+proliant]("http://www.ubuntuforums.org/showthread.php?t=255335&page=2&highlight=compaq+proliant")

---

