---
title: "Login problem after minor update 12.04 LTS"
date: 2012-07-08
forum: Installation &amp; Upgrades
---

### Post by Peet on 2012-07-08
Hi,

More info, in case it helps: Linux 3.2.0-26-generic x86_64

I have been enjoying reasonable stability on 12.04, after some previous problems, and finding a way to get some form of usable menu that one can get a list of applications, instead of having to search for each app you hope you have.  Not the point really, I realise some are smarter than me with these things!

So I perform a "mark all updates" in Synaptic yesterday, not paying too much attention to all of them.  Afterwards the machine became unstable - there were some Kernal files, so not too surprising, I restart my machine.

Now it boots fine, up to graphic login prompt, but when I put my password in it goes briefly to a terminal view, then comes back to asking for my password, restarting X does the same.  I suspect X is not fully starting somewhere, but unsure what to do about it.

It seems a shame to re-install from scratch for what I think is a minor issue, yet I cannot find anything on this problem in the forum, and that is my main PC!  A fresh install may mean I can get VMware working again, which worked beautifully on my previous versions.

Thanks in advance for any help
Peet

---

### Post by Peet on 2012-07-09
Any advise would be welcome!

What command line command can I use to force X to reconfigure itself?  Hoping that is the problem!

---

### Post by dino99 on 2012-07-09
cant you get a terminal to run some commands ? or boot into recovery mode ?

which desktop  is it ? gnome ? which graphic driver used ? real install or virtual ?

---

### Post by Peet on 2012-07-09
Hi Dino99,
I can get into terminal (CTRL ALT 1), no problem, just not graphic.  I am using KDE, Nvidia drivers, though I am not sure if I am using real or virtual, I have to admit little technical Linux knowledge, though using Ubuntu for at least 5 years!
I have run apt-get update / apt-get upgrade, all reported as up to date.
Regards
Peet

---

### Post by Peet on 2012-07-10
Hi,
It would be great if I can get a command to reconfigure X, which may be my problem.
Thanks
Regards
Peet

---

### Post by bogan on 2012-07-10
Hi!, **Peet**,

I do not know if it is what you need, but this is what you asked for:

Check in Synaptic Package Manager exactly what is installed, with "xorg" as Quick Filter,

Probably 'xorg', 'xserver-xorg' and 'xserver-xorg-core'; substitute each of their names in place of: '<packagename>' in the following:```
sudo dpkg-reconfigure <packagename>
# EDit2: There are many other 'xserver-org-*' packages installed so you could try
# that as well, before the following:
```If that does not work you could try:```
 sudo dpkg-reconfigure -a # checks all packages
```or: ```
sudo apt-get install -f.
```Before you do so, re-run ```
sudo apt-get update.
```The 'dpkg -a' command will probably take a long time with no feed back - if there are no errors found -  just wait it out, maybe 20 minutes; alternatively - and I have no idea why - sometimes it asks for all sorts of interactive choices, just press 'Enter', unless you know what else to put in.

Edit: **Afterthoughts**:

[I]Have you tried to log-in as 'Guest'? or renaming the .ICEauthoirity file?

There are other possible causes: 'lightdm' or the 'greeter', need for 'nomodset' in the Linux boot line, amongst them, see other Posts,[/I]

Chao!, **bogan.**

---

### Post by Peet on 2012-07-10
I have tried another account - same problem, it's as if X crashes and restarts, giving the login prompt again. Will try the commands tomorrow, thanks for that!

---

### Post by Peet on 2012-07-11
OK,

It was not reconfigure.  Ran dpkg-reconfigure -a, rebooted.  Still only get back to login prompt.  Same as "restart X server (ALT+E)"

I guess a fresh install is the only option I know of now.
Thanks for the assistance.

---

### Post by bogan on 2012-07-11
Hi!, **Peet,**

Have you tried the other options in the 'Afterthought' to my earlier post? #6.

Chao!,**bogan**.

---

### Post by Peet on 2012-07-11
Hi Bogan,

I have tried logging in with another account, with the same results.

Is there a guest account, if I have not set one up?  What password?

Where can I find .ICEauthoirity?  I always install MC as soon as I have a live system, so navigating files... is no problem.  I suppose MC should be able to search for it as well.

I will add nomodset to the boot options to see if that works.

Thanks
Regards
Peet

---

### Post by bogan on 2012-07-11
Hi!, **Peet**,

Assuming you are using Ubuntu, and not one of the alternative installations, there is normally an option in the log-in screen to choose a 'Guest' account, and it is set to not require  a Password.

If you create one, as far as I remember, it asks for a password but you can click on the '>' symbol at the end of the string box for password entry and it will then operate without one. BUT, of course, it will not have sudo access. 

You will find: ' .ICEauthority' in the 'HOME' folder by selecting 'Show Hidden Files' in the View Menu [ or 'Ctrl+H ']. ie, in /home/username/. ```
sudo mv  /home/username/.ICEauthority /home/username/.ICEauthority.old # or some such name
```and then reboot.

I do not use MC, but I presume it will allow you to remame the file, though you may need to use 'gksu MC'.

Chao!,** bogan**.

---

### Post by Peet on 2012-07-11
Hi,
Tried adding "nomodset" in boot string, I have renamed IECauthority & rebooted (one great convenience when I log into text mode is sudo mc, which sets me up with a file navigator, and root privileges).  I am using Ubuntu, yet I could not get any luck with guest.  I do have 2 user accounts, though same result on each.  I also get the same result selecting different desktops, even recovery desktop environments. So far nothing has made a difference. Tomorrow I will search for posts on 'lightdm' or the 'greeter', to see if they may indeed be affecting me.
Thanks
Regards
Peet

---

### Post by bogan on 2012-07-12
Hi!, **Peet**,

If you are still of the opinion that your problem stems from something amiss with Xorg or xserver, Update manager is currently updating both 'xserver-common' and 'xserver-xorg-core'.

So you might want to be sure you have tried them.

Chao!,** bogan**.

---

