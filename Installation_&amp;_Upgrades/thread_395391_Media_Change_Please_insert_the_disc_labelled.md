---
title: "Media Change: Please insert the disc labelled"
date: 2007-03-28
forum: Installation &amp; Upgrades
---

### Post by tatster on 2007-03-28
Hi,

I have just installed Edgy server 6.10 on a box at home.  I am trying to install build-essential group of packages but I get the message

```

Media Change: Please insert the disc labelled
 âUbuntu-Server 6.10 _Edgy Eft_ - Release i386 (20061025.1)â
in the drive â/cdrom/â and press enter
```

However - I am not at home and don't have physical access to the box now. (I can SSH to the box over the internet.)   Is there anyway round this?

Thanks,

Tat.

---

### Post by tatster on 2007-03-28
I fixed it!

For others who find this thread.....
You have to comment out the cdrom reference in /etc/apt/sources.list

And then it works.

Tat.

---

### Post by maiios on 2007-03-29
Great timing! I was just looking for this information. Thanks!

---

### Post by Ek0nomik on 2007-07-16
Thanks tatster.  ;)

---

### Post by dcorwin822 on 2007-07-21
+1 thanks a bunch!

---

### Post by mirzmaster on 2007-08-04
Thanks!  I had this problem on my Feisty server just now, and this tip resolved the issue  :)

By the way, I suspect the cdrom statement is added after a kernel version upgrade.  I had just performed a dist-upgrade a short while before, so in my sources.list file I found multiple cdrom statements, with one that had already been commented out (presumbly it's commented out by default when you install Ubuntu).  Looks like the second, uncommented cdrom statement is added when doing a dist-upgrade.

Again, thanks for the solution!

---

### Post by jimmy_chu on 2007-08-13
Thanks. I am also looking for this info. :KS

---

### Post by Joshua FUrlow on 2007-09-08
Thanks this was a great help as i set up a server but used a drive from another pc and had to put it back so there was no way of putting a disc in also it saves time as the internet is just as fast.

---

### Post by rearviewmirror on 2007-10-26
I ran into this as well.  Here's a bit more detail:

/etc/apt: cat sources.list | grep cdrom

deb cdrom:[Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

Two lines exist, one is already commented out.

If you want to add the cdrom back in there run ```
apt-cdrom
```

When finished run:  ```
sudo apt-get update

```

---

### Post by crozar on 2007-11-10
please some1 explain this , i have this error  aswell and i want to install some initials but i cant because it ask for a cd , the tutorial up doesnt make sense i typed in terminal 
/etc/apt/sources.list and it didnt work :(

---

### Post by tatster on 2007-11-11
Hi,

I'll try and explain in a bit more detail what I did - which worked for me.

If you are not familiar with editing files from within the terminal, you can try this....

Open Terminal, and enter:

sudo gedit /etc/apt/sources.list

This should open up a text editor and you should see the contents of the sources.list file.
Find any entries that start with deb cdrom:  simply put # at the beginning of that line, save the file and then try again.

Hope this makes sense, and helps you!  If not, post back and we'll see what we can do.

Tatster.

---

### Post by benjerman on 2007-12-03
> **tatster said:**
> I fixed it!

For others who find this thread.....
You have to comment out the cdrom reference in /etc/apt/sources.list

And then it works.

Tat.

I love you.

---

### Post by Drostman on 2008-01-22
> **crozar said:**
> please some1 explain this , i have this error  aswell and i want to install some initials but i cant because it ask for a cd , the tutorial up doesnt make sense i typed in terminal 
/etc/apt/sources.list and it didnt work :(

thats because /etc/apt/sources.list is trying to execute the file and it is not executable.  You need to edit the file 

in command line

```
sudo nano /etc/apt/sources.list 
```

then in that file comment out the line that #deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) etc..

```
sudo apt-get update
```

and you should be good

---

### Post by dannyboy1121 on 2008-04-04
tatster .. you're a dude

---

