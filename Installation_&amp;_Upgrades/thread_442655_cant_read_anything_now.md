---
title: "cant read anything now"
date: 2007-05-13
forum: Installation &amp; Upgrades
---

### Post by elj4176 on 2007-05-13
I tried an upgrade today and now I cannot read anything. The only character that is being displayed is  a square. I can ssh into the box and all is well but the gui is 'gunked' up. 
Any help would be appreciated before I wipe the drive and start over.
I already tried 
dpkg-reconfigure xserver-xorg 

and i also tried 
sudo aptitude install msttcorefonts 

and rebooted to no avail. 
THanks!

---

### Post by elj4176 on 2007-05-14
Well - I'll just wipe the drive and start over. Much easier than trying to sort out that non-sense.

---

### Post by bulldog on 2007-05-14
You have to admit that saying 'I tried an upgrade today and now I cannot read anything. ' isn't much info at all.

Tell what kind of upgrade you did,and why you think it messed your fonts.
Now we're only guessing,and nobody has a n answer for you.:)

Did you try```
sudo dpkg-reconfigure fontconfig
```

---

### Post by elj4176 on 2007-05-22
Yes I do admint that I did not give much info. 
After some more searching I see that I am not the only one having this problem. It's seems that it is a problem with apt (or aptitude) not being able to complete the update process. I tried to update a perfectly working dapper box to feisty since the 'recommended ' method to upgrade to edgy failed. I used :
gksu "update-manager -c"
and got an error message saying could not calculate the upgrade. I then decided to go straight to feisty by changing sources file and running :
sudo aptitude update
sudo aptitude dist-upgrade

Then I get the squares instead of characters. I also tried the alt-cd upgrade method but without being able to read the text in the command buttons/windows it was nearly impossible. 
I rarely use the gui on that box anyway and since the server seems to be serving webpages and files ok and the comand line works - I'm not going to worry about it for now.

---

### Post by elj4176 on 2007-08-13
still no answer for this problem? Re-install is not a good answer either.

---

