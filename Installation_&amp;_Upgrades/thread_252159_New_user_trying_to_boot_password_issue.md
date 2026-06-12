---
title: "New user trying to boot password issue"
date: 2006-09-06
forum: Installation &amp; Upgrades
---

### Post by Dragonfire1 on 2006-09-06
New user trying to boot password issue 


 
I'm trying to boot the Ubuntu I remember the passwords but it wont take it. I did the 6.06.1 LTS Daper Drake Desktop did format I have been playing around with commands while working at this. I do have my win 98 sytem that will still boot but would surely like to try this.
It appears it recognizes me so after the $ it won't take the new password after the $ I set up. 
Maybe I'm missing a command new to this.
I also palyed around with sudo etc. 
Any help would appreciate.

I'm wondering now to figure out how to do an unistall.

Thanks
Dragon

---

### Post by taurus on 2006-09-06
If you don't remember your password and would like to changet it, boot into recovery mode (from GRUB menu) and at the prompt, type

```
passwd john
(assuming john is your login name)
```
Once you have entered the new password (twice for confirmation), reboot and log in with the new password.

---

### Post by Dragonfire1 on 2006-09-06
I just tried twice to boot on recovery.
In Grub as you mentioned.
Says Give root password for maintenance
or type Control-D to continue then the cursor keeps blinking won't let me enter anything.
Thanks.

---

### Post by mssever on 2006-09-06
Perhaps you have/had caps lock on? Passwords in Linux are case sensitive. Did you set up a Grub password? There isn't one by default. And did you try Ctrl+D?

In Grub, you should be able to hit the down arrow until you get to the recovery mode and hit enter. When it comes up, type```
passwd yourusername
``` This will reset your password. You can find your username by typing ```
ls /home
```

Then, switch to normal mode. Type ```
telinit 5
```

---

### Post by Dragonfire1 on 2006-09-06
Appreciate the help you gave.

Its just work for me to get in.
Prompt will not let me even to type the other commands.
I have messed around with this and have read.
I probable shouldn't have left the Win on it prior to install.
I wrote down all my passwords when installing alway's do. Maybe a letter got thrown off for password. Tried caps other letters around the key.
Thanks,

---

### Post by mssever on 2006-09-06
OK, so Grub won't even let you choose recovery mode? Then I have another idea. (BTW, I don't think that this problem has anything to do with dual-booting Windows.)

Boot from the live CD and mount your Linux partition. I'm not sure if there's an icon for this or not on the live CD. But you could try it from the terminal. I'm assuming that you took the defaults during install, you have only one hard disk, and that your Linux partition is hda2. If it isn't try hda1, hda3, etc. If your partition is on the second disk, then it would be hdb1 or hdb2, etc.

```
sudo mount -t ext3 /dev/hda2 /mnt
``` 
If you need to unmount the partition (eg if you mounted the wrong one), do ```
sudo umount /mnt
``` 
Now, type ```
echo "a temporary password of your choice" | md5sum
``` and copy the result (don't include any spaces or characters after the spaces).

Next, open up your shadow file:
```
cd /mnt/etc
sudo cp shadow shadow.bak
sudo gedit shadow
``` 
Each lines is divided into fields by colons (:). Find the line with your username and delete the second field ONLY. Put in that field $1$followed by the hash you copied. For example, if your temp password was password, you would put ```
$1$286755fad04869ca523320acce0dc6a4
``` Save and reboot. You should be able to log in now. You should also change your password now the canonical way.

---

### Post by mssever on 2006-09-07
Quote from PM:
[quote=Dragonfire1]Thanks appreciate for your help.
I will try to figure this out every morning.
I seems to recognize me in the terminal.

It shows something like this.
I have been trying to see what comes up.
I can see bash history .bash_profile directory in blue.
.bash_logout .bashrc  .sudo_as_admin_sucessful
me @ Me: ~$ pwd
/homeself
me @ Me :~$   cursor still blinks I wonder what it is looking for to start the Xwin or open it up.

I think this is the way it is partioned. 

I didn't go through your other steps as yet.[/quote]
[SIZE=2]*(I pasted the relevant part from your PM here because a) I couldn't find a reply button on the PM screen, and b) it will make it easier for others to follow along.)*[/SIZE]

I take it that you can log in, then--but you only get a command prompt without a graphical interface? If so, type "startx" and see what happens. Please post back any error messages you get. If X doesn't start and you don't see error messages, then look in .xsession.errors:
```
less .xsession-errors
```

---

