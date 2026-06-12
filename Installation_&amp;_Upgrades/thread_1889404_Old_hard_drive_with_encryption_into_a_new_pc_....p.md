---
title: "Old hard drive with encryption into a new pc ....please help"
date: 2011-12-01
forum: Installation &amp; Upgrades
---

### Post by chillheffuk2004 on 2011-12-01
Hi

My dell pc recently died beyond worthwhile repair. I am now trying to copy all my old files from the home directory and transfer to an external drive. Then i can drop them onto a nice new shiny formatted ubuntu desktop pc. 

This is becoming a bit of an issue. I thought if i ran live cd from a usb stick, i could mount the drive, copy my files and paste them somewhere sensible. However, the home folder still has the encryption on it from my old pc install. i still have the password ( i hope) but is there anyway i can bypass the encryption? Failing that how do i tell it i know the password?

Any help would be greatly appreciated.

many thanks

---

### Post by Lampi on 2011-12-01
what's the encryption like?
luks? ecryptfs? encfs?

---

### Post by Lampi on 2011-12-01
ah what the hell I bet it's ecryptfs, so try this:

- boot live cd again
- mount the partition where your encrypted home is
- type "sudo ecryptfs-recover-private" in a terminal

that should trigger a search for encrypted directories and report success:

> 
INFO: Searching for encrypted private directories (this might take a while)...
INFO: Found [/media/<your partition>/home/.ecryptfs/<username>/.Private].
Try to recover this directory? [Y/n]:

you proceed then as prompted, it will ask for the enc password and you're done, it's open.

---

### Post by chillheffuk2004 on 2011-12-01
i am trying that as we speak, thanks for the replies :D

---

### Post by chillheffuk2004 on 2011-12-01
SUCCESS! PRIVATE DATA MOUNTED READ-ONLY AT XXXX. 

thanks for that. Can i lose the read only permissions as i assume i wont be able to copy the files. (still loading so i cant try it yet)

---

### Post by Lampi on 2011-12-01
you should be able to copy them to your new install no matter what. It's kind of a safety precaution, so you enc data is protected. You don't need write privileges to copy files, but you might need sudo if some files belong to another user and the file is unreadable for "others"

---

### Post by chillheffuk2004 on 2011-12-01
it's just sat there in the home folder saying loading at the moment. It's either genuinely loading or something isnt quite right. I guess it could just be taking awhile.

---

### Post by Lampi on 2011-12-01
yeah, it might speed things up if you append the mountpath:

```
sudo ecryptfs-recover-private [encrypted private dir]
```

[encrypted private dir] can be /media/sdb3 for example (where ever you mounted your enc home)

---

### Post by chillheffuk2004 on 2011-12-01
i am going to expose my newb ness here. Im not too sure where it is mounted. I just hit Y to recover. It still doesnt appear to be loading and whenever i try to find anything, it moans about permissions :(

---

### Post by Lampi on 2011-12-01
it's somewhere in /tmp/ecryptfs.XXXXXXXX.

"mount -l" will tell you where exactly, as will ecryptfs-recover-private if you read the pointers that script gave you again

---

### Post by chillheffuk2004 on 2011-12-01
i stopped being silly and re-read your previous post and indeed found the folder (yay). It is all still there, however when i try to paste it somewhere else, i am now getting this error "the folder nepomuk cannot be handled because you do not have permissions to read it". Thank you again for all your help.

---

### Post by Lampi on 2011-12-01
like I said you need sudo to read some files:

if you're in gnome/unity:
```
gksudo nautilus /tmp/ecryptfs.XXXXXXXX
```
or if you're in kde:
```
kdesudo dolphin /tmp/ecryptfs.XXXXXXXX
```

---

### Post by chillheffuk2004 on 2011-12-01
you sir are an absolute legend. My files are copying to another hdd as we speak. the problem was that the live cd install i am running has no form of nautilus in it. So i downloaded it from the upgrade centre, then ran your command above and voila. I can now crack on with my new pc build. (fingers crossed). Thanks a lot for your help, its really appreciated. (apologies for the lack of knowledge in certain aspects).

---

### Post by Lampi on 2011-12-01
what's that cd like, that comes without a file manager? is this an ubuntu cd? it kinda has to, otherwise it won't have the ecryptfs-recover thingy...

... little strange, but it's nice you got it sorted :)

---

### Post by chillheffuk2004 on 2011-12-01
its a bootable usb job (one i knocked up ages ago). god knows what version is actually on it. sorted in the end though. thanks again

---

