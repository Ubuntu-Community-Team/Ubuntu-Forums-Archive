---
title: "Cannot access /home partition after reinstall"
date: 2009-12-19
forum: Installation &amp; Upgrades
---

### Post by goosenoose on 2009-12-19
I shouldn't have lost my patience.

I upgraded to Xubuntu 9.10 a few days ago. Prior to the upgrade, I was having issues with Firefox (small issues, such as not being able to press enter in the top right search box and such). After the upgrade, I began to have issues with read/write permissions from Firefox. 

My actions from that point were to reinstall from my Jaunty alternate disk.

My partitions are:
/, /home, and /swap.

On my reinstall I formatted and installed to the / and /swap partitions and set my installation to reuse my /home partition as my /home directory.

I cannot log in. I receive a message saying something like "You were logged in for 10s or less..." The detailed err output contains multiple messages that say that the system was unable to write/create new folders (Documents, Music, etc..) to /home.

I was able to log in with the failsafe terminal, however, I cannot do anything that requires writing to the /home directory.

I have data that I do not want to lose on my /home. Any and all help would be appreciated.

---

### Post by goosenoose on 2009-12-19
update:

so, i'm biking between my apartment and the library to get online...

the username that i registered on reinstallation is the same as the one i had prior to reinstall.

i'm was advised that i had to check the user-id of the directory/ownership and whether or not it's owned by 'root'... not sure how to do this, researching for the time being.

note - i do remember running that 'encryption' feature way back when after my first installation... could this be preventing my access?

---

### Post by phillw on 2009-12-19
> **goosenoose said:**
> update:

so, i'm biking between my apartment and the library to get online...

the username that i registered on reinstallation is the same as the one i had prior to reinstall.

i'm was advised that i had to check the user-id of the directory/ownership and whether or not it's owned by 'root'... not sure how to do this, researching for the time being.

note - i do remember running that 'encryption' feature way back when after my first installation... could this be preventing my access?

"encryption feature " would certainly stop you accessing it. Another one that can cause problems is not just the user name, but the actual UID - which can be different accross installs.

Assuming that /home is on /dev/sda9   (replace the 9 with what ever it is)

Boot with the LiveCD, drop to terminal
```
cd /
sudo mkdir /new
sudo mount /dev/sda9 /new
```

then cd'ing to /new and see if you can ls your files and directories - regardless of ownership

you may have to issue sudo cd  and sudo ls !!

Phill.

---

### Post by goosenoose on 2010-02-28
update:

so.. i've botched things up a bit. fie, human error.

reinstalled using a live disk. accidentally formatted the encrypted partition where the last three years of my life have been stored.

however, learning experience (backing things up now -_-)... 

and.. testdisk/photorec. very interesting stuff.
and.. **encryptedPrivateDirectories. **

So what I'm trying to do now is mount my (formatted) encrypted  partition through ecryptfs [(link)]("https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering Your Data Manually") with the idea that testdisk might find something if the drive is searched with correct decryption passphrase on assigned. 

What my problem is: the encrypted partition does not show up in the /media even though I can clearly see it in nautilus when I go to the /media folder.

Why can't I see this partition in my terminal?

---

