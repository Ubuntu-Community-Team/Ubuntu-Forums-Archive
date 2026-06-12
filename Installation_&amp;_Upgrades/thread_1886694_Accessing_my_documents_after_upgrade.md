---
title: "Accessing my documents after upgrade"
date: 2011-11-25
forum: Installation &amp; Upgrades
---

### Post by najim on 2011-11-25
Hello 

i recently made an upgrade which seemed to have gone good but turned to be bad, from 10.10 i made online upgrade to 11.04 and everything went on smooth but after restart Gnome terminal could not work, then trying to fix gnome terminal crashed my synaptic tool and i had to use a 11.10 CD to fix the problem because i thought it would save because of being the latest release.

in all i only managed to install 11.10 alongside the other older ubuntu version which can't at the moment start up, using 11.10 i can start my machine properly but now i need a way of accessing my documents in the older install (10.10), any ideas on how i can go other this issue.

all other files/document on non root partitions are intact and not affected my the upgrade

Regards

---

### Post by dabl on 2011-11-25
Just mount the partition that has the 10.10 OS on it.  I assume you mean there are documents on that partition with the OS:

So, if it is /dev/sdc then you do these things:

1. make a mount point

sudo mkdir -p /mnt/SDC

2. mount the partition

sudo mount -t ext4 /dev/sdc /mnt/SDC


Now you can use your file manager and copy the data files out of the directory /home/najim that you find on the mounted filesystem under /mnt/SDC.

---

### Post by ajgreeny on 2011-11-25
You should still be able to mount and read all the files and folders in your old home folder without a major problem.

Open up nautilus with command ```
gksu nautilus
``` and it ought to show all the partitions available in its left hand pane.  Click on the partition that is your old installation and navigate to the /home folder, from where you will be able to copy all the files and folders to another partition or external drive.  Don't forget the hidden files and folders as well.

You can copy all those back to your new /home in the same way, but you may then need to run ```
sudo chown -R *username:username* /home/*username*
``` where username is your own user, and possibly also ```
chmod -R 755 /home/*username*
``` This second command should not need sudo, as you will already own the files and folders following the first *chown* command.

Bear in mind that there are some big differences in the configurations etc etc for gnome3 applications compared with gnome2, so it's possible that some of those hidden files and folders may cause problems;  you may wish to try copying them across one by one just in case.  I am not using 11.10, so I'm not sure about these potential difficulties when using old configuration files and so on.

EDIT:
If you still have the same username as before, you may be able to do what dabl says.  I didn't think quickly enough!

---

### Post by najim on 2011-11-25
Thank you so much [dabl]("http://ubuntuforums.org/member.php?u=217451") and [ajgreeny]("http://ubuntuforums.org/member.php?u=27747")

after running the command 

```
gksu nautilus
```
i managed to navigate to the folders which where restricted in the first place, but i forgot to mention i had made my files private on installing 10.10 and probably encrypted if i remember very well and right now inside my old home /home/najim there are  two folders najim & .ecryptfs and inside ecryptfs is another folder najim {/home/najim/.ecryptfs/najim} and inside this are two other folders .ecryptfs and .Private  

The folder .Private has lots of files inside it and i think this is my [ Documents ].
Now how can i get to read them in a normal form i mean something like decrypting these files.

---

### Post by ajgreeny on 2011-11-26
Sorry, but I can't help here at all.

These sort of problems are exactly the reason why I have always been so afraid of encrypting my /home partition, and just make sure I have both good physical and strong password security measures set.

I am sure there must be ways to get to your files etc etc even on an encrypted partition, but it will depend you knowing the password, or key you set at the time you set it up.  If your only record of that is on the encrypted partition, and you can not remember it, you may be out of luck.

---

