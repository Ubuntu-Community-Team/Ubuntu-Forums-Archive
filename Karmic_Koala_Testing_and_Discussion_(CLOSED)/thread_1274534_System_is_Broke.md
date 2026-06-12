---
title: "System is Broke"
date: 2009-09-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tjeremiah on 2009-09-24
This morning I tried to update but the system wouldn't update, even via terminal. I reboot and everything is dead. The system stalls on crypto check.

I basically describe it here but people are ignoring the thread allowing it to end up on page 3 :(. Seriously I need help.

[http://ubuntuforums.org/showthread.php?t=1274260](http://ubuntuforums.org/showthread.php?t=1274260)

---

### Post by terry_gardener on 2009-09-24
are you able to boot using the recovery option
is so you can update from there 
if not boot from live cd and update from there.

to update from live cd check the following pages

[http://ubuntuforums.org/showthread.php?p=7952958#post7952958]("http://ubuntuforums.org/showthread.php?p=7952958#post7952958") 

[http://ubuntuforums.org/showthread.php?t=1267040](http://ubuntuforums.org/showthread.php?t=1267040)

---

### Post by VMC on 2009-09-24
> **tjeremiah said:**
> This morning I tried to update but the system wouldn't update, even via terminal. I reboot and everything is dead. The system stalls on crypto check.

I basically describe it here but people are ignoring the thread allowing it to end up on page 3 :(. Seriously I need help.

[http://ubuntuforums.org/showthread.php?t=1274260](http://ubuntuforums.org/showthread.php?t=1274260)

Can you get to recovery mode. Put the word "single" at the end of kernel line.

---

### Post by tjeremiah on 2009-09-24
nope, cant access recovery mode because crytpo wont finish "loading." Tried going into text, samething, etc.

---

### Post by tjeremiah on 2009-09-24
I dont have a LIVE CD, how do I get without waiting for one in the mail ? I feel like just starting over, where can I go to get the most updated installs of karmic?

EDIT: Im dling the daily build of karmic now. I guess that can be considered a LIVE CD

---

### Post by terry_gardener on 2009-09-24
if you dont have live cd then i guessing you upgraded the from the previous version. 
if you have the jaunty live cd this will do also. 
if you dont have any live cd or live usb. ask a friend or family member to download one and burn it to disc, if at all possible.

---

### Post by Vanishing on 2009-09-24
> **tjeremiah said:**
> nope, cant access recovery mode because crytpo wont finish "loading." Tried going into text, samething, etc.

try this:

> 
after you see that crytpo thingy,wait for 5 - 10 secs, then
alt + prt sc + R S E 
then input your password
then you should be able to get a shell.

---

### Post by tjeremiah on 2009-09-24
> **terry_gardener said:**
> if you dont have live cd then i guessing you upgraded the from the previous version. 
if you have the jaunty live cd this will do also. 
if you dont have any live cd or live usb. ask a friend or family member to download one and burn it to disc, if at all possible.

ok but isnt a LIVE CD an Ubuntu installation disk ? Because if so I can make one no?

Sorry, just need clearer confirmation.

---

### Post by tjeremiah on 2009-09-24
> **Vanishing said:**
> try this:

ok I will after the download.

---

### Post by forumache on 2009-09-24
> **tjeremiah said:**
> ok but isnt a LIVE CD an Ubuntu installation disk ? Because if so I can make one no?

Sorry, just need clearer confirmation.

Yes, the "desktop install" Ubuntu disk is a LiveCD.
"Alternate desktop install" does not work as LiveCD.

If you formated the disk as ext4, you need a Karmic LiveCD.
Otherwise, you can use Jaunty if you have one and don't want to burn a Karmic.

---

### Post by tjeremiah on 2009-09-24
> **Vanishing said:**
> try this:

ok, got that :) BUT when I run apt-get update, it doesnt pull anything in. Im connected via ethernet.

---

### Post by kansasnoob on 2009-09-24
Not sure I understand:confused:

So you're just running apt-get update from the live CD?

If you want to update an existing installation using the Live CD you have to mount and chroot into that system. Look at my post #6 here:

[http://ubuntuforums.org/showthread.php?t=1274335](http://ubuntuforums.org/showthread.php?t=1274335)

---

### Post by tjeremiah on 2009-09-24
> **kansasnoob said:**
> Not sure I understand:confused:

So you're just running apt-get update from the live CD?

If you want to update an existing installation using the Live CD you have to mount and chroot into that system. Look at my post #6 here:

[http://ubuntuforums.org/showthread.php?t=1274335](http://ubuntuforums.org/showthread.php?t=1274335)

Oh, I thought once I did what the user suggest, to solve the problem , I just had to update the system :( Also, do I just go into the terminal with the LIVE CD? Like where do I input the commands?

---

### Post by kansasnoob on 2009-09-24
> **tjeremiah said:**
> Oh, I thought once I did what the user suggest, to solve the problem , I just had to update the system :( Also, do I just go into the terminal with the LIVE CD? Like where do I input the commands?

Applications > Accessories > Terminal.

Aren't Alphas fun?

There has been a lot of breakage in the past couple of weeks but Karmic is seeing huge changes - truly bleeding edge stuff!

Alphas are not really for noobs:)

---

### Post by VMC on 2009-09-24
> **tjeremiah said:**
> Oh, I thought once I did what the user suggest, to solve the problem , I just had to update the system :( Also, do I just go into the terminal with the LIVE CD? Like where do I input the commands?

Did you get a prompt from your karmic installation? If so you don't need to chroot your already there. Since you used your login you need to add sudo in front of the command:

```
sudo apt-get update && sudo apt-get dist-upgrade

```

---

### Post by tjeremiah on 2009-09-24
> **kansasnoob said:**
> Applications > Accessories > Terminal.

Aren't Alphas fun?

There has been a lot of breakage in the past couple of weeks but Karmic is seeing huge changes - truly bleeding edge stuff!

Alphas are not really for noobs:)

my Karmic broke before. I find it fun doing these things, it helps me learn more. Been with Karmic since the first alpha.

---

### Post by tjeremiah on 2009-09-24
> **kansasnoob said:**
> Not sure I understand:confused:

So you're just running apt-get update from the live CD?

If you want to update an existing installation using the Live CD you have to mount and chroot into that system. Look at my post #6 here:

[http://ubuntuforums.org/showthread.php?t=1274335](http://ubuntuforums.org/showthread.php?t=1274335)

ok, I did everything you said, but here is the problem.

When sudo mount /dev/sda3 /mnt
even though its the right path, it tells me to specify 

So i went ahead and tried sda5 and it tells me its already mounted.
I continue on with the "already mounted" sda5 and every command gives me no feedback.
Go along with gedit /boot/grub etc after chroot and it saids it cant display. :(

Should I just start over, fresh install? Is it possible for me to keep my files/settings?

---

### Post by tjeremiah on 2009-09-24
images:

---

### Post by kansasnoob on 2009-09-24
> **tjeremiah said:**
> ok, I did everything you said, but here is the problem.

When sudo mount /dev/sda3 /mnt
even though its the right path, it tells me to specify 

So i went ahead and tried sda5 and it tells me its already mounted.
I continue on with the "already mounted" sda5 and every command gives me no feedback.
Go along with gedit /boot/grub etc after chroot and it saids it cant display. :(

Should I just start over, fresh install? Is it possible for me to keep my files/settings?

Well, it looks like sda5 should be right:

```
sudo mount /dev/sda5 /mnt
```

but then you must follow thru with each command.

---

### Post by tjeremiah on 2009-09-25
> **kansasnoob said:**
> Well, it looks like sda5 should be right:

```
sudo mount /dev/sda5 /mnt
```

but then you must follow thru with each command.

If I could kiss you, I would :P . It worked ! THANKS!!:guitar:

---

