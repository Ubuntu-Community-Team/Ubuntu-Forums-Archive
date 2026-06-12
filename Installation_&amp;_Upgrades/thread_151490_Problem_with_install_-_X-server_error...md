---
title: "Problem with install - X-server error.."
date: 2006-03-28
forum: Installation &amp; Upgrades
---

### Post by envytwo on 2006-03-28
Hey guys, Ive been trying for the last few nights to install ubuntu with no luck.  

The computer I'm trying to install it on is an HP Pavillion a1130n, AMD 64, 3500.  2gigs of ram,  Ati pro x700 video card, and a 250gig, those are my specs, I hope this will help you guys help me!

When I get the error,  I type "sudo dpkg-reconfigure xserver-xorg"  I go through everything, and to begin with I selected Vesa,  then tried to restart x by typing "sudo /etc/init.d/gdm start" (not sure if thats right) and it says failed. ( I also did these steps selecting ATI instead of VESA)

If I try restarting my pc, it goes through the ubuntu start up screen, then when its done, screen turns black with a white blinking "_" then it stops and thats it, cant do anything after that.  

What sucks is that I can run Knoppix live cd, and Kororaa live cd (which is awesome btw :)  ).  But I would realy like ubuntu to work, I dont want to have to install windows again :)

Thanks in advanced for the help! I'll be checking here all night till I cant stay up, hopefully fix this before bedtime!

---

### Post by envytwo on 2006-03-28
I've looked through other posts today, and I still cant find anything to help :(

If anyone has any other tips, please let me know!! I want to play with ubuntu!! :)

Thanks in advanced!!!

---

### Post by RRS on 2006-03-28
You might consider running the 32 bit instead of 64.

Had problems with X myself when I installed the 64 bit version on my AMD machine but 32 runs fine.

From browsing the forums I have the impression this is somewhat common with Breezy but should be fixed with Dapper.

Also, try "start x" 

Hope this helps.

---

