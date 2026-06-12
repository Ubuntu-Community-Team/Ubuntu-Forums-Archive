---
title: "Can't install Ubuntu"
date: 2004-12-06
forum: Installation &amp; Upgrades
---

### Post by stking on 2004-12-06
I've burned the iso cd for Ubuntu and when I try to install it, nothing happens
I get a flashing curser in the upper left corner. I've actually burned thre CD's and downloaded the file at least twice thinking that maybe there was a problem with the file or the CD burn.
Doesnt matter Still nothing.
I have other Linux distro's that I have successfully burned and installed.

Thanks for your help
Steve

---

### Post by Hikaru79 on 2004-12-06
Hm. I was going to suggest that perhaps your BIOS wasn't seet to boot from CD, but you say you've installed other Linux distros so that's probably not the issue.

And I'm not going to insult you by suggesting that you burned the .iso as a file rather than as an image.

So, if neither of these apply, I have no clue :(

---

### Post by stking on 2004-12-06
Well, I probably did burn the iso as a  file.
I just copied it to the cd 
And when I try to view the cd directory it just locks up
So perhaps you could clue me in on how to burn the iso as an image.
Apparently I've done it once but don't remember what I did diferently
Thanks for your help
Steve

---

### Post by Rancoras on 2004-12-06
What burning app do you use?

---

### Post by alainhenry on 2004-12-07
You could use cdrecord from the command line 

1) cdrecord --scanbus

to know the SCSI info for your drive, and then something like 

2) cdrecord -o speed 8 dev=0,0,0 data image.iso

I am on a windows only machine right now (apologies) , and don't remember the exact syntax.  You'd better check the man page before using this

man cdrecord

in the command line, speed must be chosen to fit your drive writing speed (8 in my case), and dev=0,0,0 should actually have the three figures you will get from the first command.  

Alain

---

### Post by alainhenry on 2004-12-07
Back on my Linux machine, the cdrecord commands I use are

cdrecord -scanbus
cdrecord -v speed=8 dev=0,0,0 -data image.iso

Better check the manpage about your configuration, anyway. 

Alain

---

