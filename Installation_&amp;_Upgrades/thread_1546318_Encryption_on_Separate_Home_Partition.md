---
title: "Encryption on Separate Home Partition"
date: 2010-08-05
forum: Installation &amp; Upgrades
---

### Post by hobo on 2010-08-05
I think I am in trouble. Any and all help is appreciated.

I have been running Ubuntu for some years now and I may have finally screwed myself.

I have been running 10.04 64 bit upgrade but decided to do a clean install. I have a separate Home partition and did not touch it during the clean install. All went well during this install until I booted to ubuntu and accessed my OLD home partition.
I HAD FORGOTTEN that I encrypted that Home. It appears that the file needed to open that Home was in my OLD system partition in /usr something. Therefore I cannot open that HOME.

Is there anything I can do to access that OLD home. I did print off the encryption key some time ago but I have no idea what I did with it.

Kirk

---

### Post by lemming465 on 2010-08-07
Don't give up yet; all may not be lost.  To give you specific advice, we need to know how the home directory was encrypted.  

I'm guessing you used "ecryptfs", from checking the "encrypt home folder ..." box when you created the user account?  If so, and if you still know the password which was used by the old user, you can recover stuff.

What you need is a new user with the same userid as the old user.  Log in as the new user, set the HOME environment variable to match the old directory, and run ecryptfs-mount-private, and supply the old password.  

Write back with more details if you need more specific directions.

---

### Post by hobo on 2010-08-09
OH great! I have done nothing yet in hopes I could find the key that was generated. I did use the default encryption used by Ubuntu.
So if I use the same PW and UID, which I did, then point the system to the old /home partition. Then 'run ecryptfs-mount-private' using the same PW it should work?
I don't want to screw this up so if you would be so kind and put the commands in this post I would feel better.
If this works I will buy the beer. That is if you drink beer.
BTW... Although I had a separate partition /home (and still do), when I did the clean install the system put /home in it's standard place.

---

### Post by hobo on 2010-08-15
bump

---

### Post by lemming465 on 2010-08-17
Sorry about the slow reply; I was experimenting with different accounts and extra meerkat alpha 3 installs, mostly without success.  What seems to work for your situation:

1) create a new user with the same user-id and password as the old user
2) modify the new user to have the same home directory as the old user

E.g. if your new ubuntu root (with on-partition /home) is /dev/sda5, and the old home partition is /dev/sda6, something along the lines of:```
sudo -i
cp /etc/fstab /etc/fstab.bak
cat >> /etc/fstab <<EOF
/dev/sda6 /oldhome ext4 defaults 0 0
EOF
mkdir /oldhome
mount /oldhome
usermod -d /oldhome/OLDUSER NEWUSER
```Now switch to the NEWUSER, and it should mount the encrypted filesystem automatically.

---

### Post by lemming465 on 2010-08-19
Note that unless the new user name, new user UID, and new user password all match the old user, some further fiddling would be required.  Also, there could be a path issue with the hidden symlinks in /oldhome/OLDUSER; you might have to recreate them pointing at /oldhome rather than /home; I think they are absolute rather than relative (possibly a bad implementation choice).

---

### Post by hobo on 2010-08-19
Advised....

---

### Post by hobo on 2010-08-25
[COLOR="Black"]Happy Days ![/COLOR] I finally had some time to devote to this problem I made and I was successful. 
What I did was disconnect every other drive connected to this computer. This was done so I would not be confused during a reinstall of 10.04. I then booted to the install disk and manually set the partitions, not formating any and pointed to the 'old home' as /home. I then installed 10.04, using the same UID and PW as before, and upon reboot I was able to read ALL the 'old home' data !

Eureka ! The beer is on me at my house for all who helped.

Thanks,

Kirk

---

