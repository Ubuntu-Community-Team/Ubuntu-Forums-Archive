---
title: "Upgrade to 10.04 alpha 3"
date: 2010-03-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by swoll1980 on 2010-03-03
I have searched, and searched for a direct path to 10.04, but can't find one. I know Ubuntu has one. Is there even a way to do this in Kubuntu, or am I wasting my time? Thanks in advance.

---

### Post by proxess on 2010-03-03
[s]just edit your /etc/apt/sources.list with your text editor (kate), change 'karmic' to 'lucid'.

Then, open um a terminal line (konsole) and update:
sudo apt-get update

and dist-upgrade:
sudo apt-get dist-upgrade[/s]

---

### Post by swoll1980 on 2010-03-03
> **proxess said:**
> [s]just edit your /etc/apt/sources.list with your text editor (kate), change 'karmic' to 'lucid'.

Then, open um a terminal line (konsole) and update:
sudo apt-get update

and dist-upgrade:
sudo apt-get dist-upgrade[/s]

Thanks. I was thinking of doing this, but wasn't sure it would work.

---

### Post by Sef on 2010-03-03
> Quote:
                                                                      Originally Posted by **proxess**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8909813#post8909813")                 
                 [I][s]just edit your  /etc/apt/sources.list with your text editor (kate), change 'karmic' to  'lucid'.

Then, open um a terminal line (konsole) and update:
sudo apt-get update

and dist-upgrade:
sudo apt-get dist-upgrade[/I][/s]
                                 
Thanks. I was thinking of doing this, but wasn't sure it would  work.That is not recommended at all.

> I have searched,  and searched for a direct path to 10.04, but can't find one. I know  Ubuntu has one. Is there even a way to do this in Kubuntu, or am I  wasting my time? Thanks in advance.
I would say you are wasting your time because even [Kubuntu's site]("https://wiki.kubuntu.org/LucidLynx/Alpha3/Kubuntu") only recommends downloading and burning a cd.

---

### Post by ratcheer on 2010-03-03
If you really want to do it (I don't recommend it if you use your PC for anything important), just type Alt+F2. In the dialog that comes up, type "update-manager -d". Then, Update Manager will start and have a button at the top to upgrade to Lucid.

Tim

---

### Post by nanog on 2010-03-03
> That is not recommended at all.

Too strong. We had a long post about this earlier in development. The long and short of it is that while it is not **supported** it should work.  In fact, this is largely what happens when you call the do-upgrade script. 

I really do not want to see ubuntu depart so far from its debian roots that you can't do a dist-upgrade.

---

### Post by tamran on 2010-03-13
[COLOR="Red"]**NOTE: Before doing the steps below, try what is in: [http://ubuntuforums.org/showthread.php?p=8961603#post8961603](http://ubuntuforums.org/showthread.php?p=8961603#post8961603)**[/COLOR]

Alright, I tried the upgrade this way and everything worked fine in the, but I would like to mention some snags/obstacles I ran into.  Nothing too sinister so if you want to do it, read on.  By the way, the machine I did this on is an HP laptop (DV5130) and the upgrade was from a fresh Kubuntu 9.10 install (so your results may vary).  Here's how it all went down:

**1) Modified the "sources.list" file:**
```
$ sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
$ sudo kate /etc/apt/sources.list
```

Then I just found and replaced all instances of "karmic" with "lucid".

**2) Update and Upgrade:** 
```
$ sudo apt-get update && sudo apt-get dist-upgrade
```

This process took a long time but [COLOR="Red"]did produce an error relating to kdelibs5[/COLOR].  The details are not so important, but was fixed using the following command (apt-get straight up said to try this):

```
$ sudo apt-get -f install
```

If this part works for you, you can then resume your update.  Again, using:

```
$ sudo apt-get dist-upgrade
```

After this step, I got all the way to the end (this step took a LONG time - several hours actually) so be patient.  Even though everything worked, there was one straggler left, leading to the next step.

**3) Fix other applications (stragglers left behind):**
It seems that the package "parted" did not want to upgrade itself due to being blocked.  This was easily fixed using the following command:

```
$ sudo apt-get install parted
```

**4) Reboot the machine:**  
Now reboot by your favorite means.  I used:

```
$ sudo reboot
```

This step had a little snag, in that the new plymouth (KMS thing) hung on the Ubuntu (yeah, not Kubuntu yet) progress screen (with the 5 dots).  I was able to send another reboot command using the power button (soft reboot, it's a laptop) and after one more reboot (and stroking the computer gently in a kind, soothing voice), it was all up and running.

**5) Profit:**
You should now be able to enjoy all the new alpha software.  Hopefully your upgrade works as smoothly.  Good luck! :)

Tamran

---

### Post by tamran on 2010-03-13
I just got another tip from the #kubuntu IRC channel in freenode to "next time" try the following command:

```
$ sudo do-release-upgrade -d
```

This is supposed to be a "cleaner" method.  For more information, try:

```
$ do-release-upgrade --help
```

If you followed the steps above this won't work, but if you're starting now give this a try.

Tamran

---

