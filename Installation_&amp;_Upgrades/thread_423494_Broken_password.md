---
title: "Broken password"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by chip616 on 2007-04-25
OK, I did some changing of user accounts, removing the original one I had.  I now log in successfully as user 1003, and attempt to use KDE's System Settings | System Administration | Users and Groups.  The admin password is requested.  I provide the valid password for the user account that I have just logged into, and no go.  It will NOT give me admin access.

Also tried the original password on the original account.  Still  no go.

So, what happened, and how can I fix it?

Thanks.

---

### Post by taurus on 2007-04-25
You need to add your username to groups **adm** and **admin** in /etc/group.  Boot into recovery mode from the GRUB menu and run

```
nano -w /etc/group
```
Save and exit with <Ctrl>0 and <Ctrl>x.

Then, reboot.

```
shutdown -r now
```

---

### Post by chip616 on 2007-04-26
Taurus:

OK, tried to do as you suggested.  Are there some commands missing in that list?  Executing

nano -w /etc/group

opens up a line in some sort of editor.  Am I supposed to add the user name to the end of that line?  When I do that and then press <enter>, it then asks me for something else -- don't remember what it is as I had to pull the removable Kubuntu drive and put in my regular one to get back to work.  Not having specific instructions from you to add the user name, I backed out.  I rebooted and tried again EXACTLY as you had laid out, and there is no change to the machine.

Thanks for your patience.

---

### Post by taurus on 2007-04-26
Can you post the output of these two commands from a terminal?

```
id
cat /etc/group
```

---

### Post by chip616 on 2007-04-26
taurus:

OK, I'm going to have to type it in by hand, as the Kubuntu machine now has no network access either, so I'm posting this from my laptop.

id command yields:

uid=1002(john2) gid=501(john2) groups=501(john2)

cat /etc/group yields a whole slew of entries which I am unable to type in fully.  Most of them appear to be stanard fare.  I am hoping the ones you want are at the bottom, as follows:

```
gdm:x:111:
admin:x:112:
john2: :501:
```

I am guessing that you are interested in the missing 'x' in the middle of the last line?

Let me know if you have to have the whole listing.  I might be able to move it to a USB device and transfer it to this machine to send it to you.

Thanks.

---

### Post by taurus on 2007-04-26
Boot your machine into recovery mode from GRUB menu.  Then, edit /etc/group

```
nano -w /etc/group
```
and add your login name, john2, to the end of **adm** and **admin**.  Save it and exit with <Ctrl>o and <Ctrl>x.  Now, see if john2 belongs to those two groups.

```
id john2
```

---

### Post by chip616 on 2007-04-26
taurus:

OK, there is an admin group, but there is no adm group.  There is root, and there is gdm.  I added john2 to admin, gdm, saved, and rebooted.

id john2

now gives the same output as before:

```
uid=1002(john2) gid=501(john2) groups=501(john2)
```

cat /etc/group gives the expected changes:

```
gdm:x:111:john2:
admin:x:112:john2:
john2: :501:
```

However,  now when I try to use KDE's Users and Groups system settings panel, I get the following error message:

```
The module Users & Groups could not be loaded
```

```
The diagnostics is:

Possible reasons:
An error occurred during your last KDEupgrade leaving an orpahned control module
You have old third party modules lying around.
```

It continues to reject the user password when asking for admin rights.

Back to you.  :)

---

### Post by taurus on 2007-04-26
Please remove the : after john2 in /etc/group.

```
admin:x:112:john2
```

The adm group is near the top of /etc/group.

---

### Post by chip616 on 2007-04-26
taurus:

> The adm group is near the top of /etc/group.

Man, how blind can a guy be?    ](*,)

OK, done.  Password now works for admin privileges.  Thanks for walking me through this.

Now, seeing as how I have already deleted my 'reference' account, I no longer know what the 'standard' set of groups are that a typical user account belongs to.  I can see how to adjust them in the KDE Users and Groups panel, but I am no longer sure which ones I should enable.  Any place I can go for this list of 'standard' groups?

Thanks again for all your help.

---

### Post by taurus on 2007-04-26
Here are the groups that I belong to on my Feisty.

```
groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),100(users),104(scanner),112(netdev),113(lpadmin),115(powerdev),117(admin)
```

---

### Post by chip616 on 2007-04-26
taurus:

Hmmm.  Smaller list than I would have thought.

Much thanks.

---

### Post by chip616 on 2007-04-26
taurus:

oooops.  Posted twice, and now can't delete it.

---

### Post by taurus on 2007-04-26
You don't have to use the whole list if you don't want.  I think you should at least belong to adm, admin, cdrom, floppy, video, audio, plugdev, & lpadmin.

---

### Post by chip616 on 2007-04-26
Got it.

So, do you do this full time for Canonical?  I am amazed at how quickly you respond, as well as the sheer number of responses you have logged.  :)

I am just starting with Kubuntu after happily using Xandros for the past 5 years.  I run Linux exclusively on 7 machines that I maintain at home and in my small business.  Xandros 4 has been a bit of a disappointment, however.  It was either Kubuntu or SuSE (I have both), and I have a preference for Debian-based rather than RPM distros, simply because of familiarity.

Frank.

---

### Post by taurus on 2007-04-26
> **chip616 said:**
> Got it.

So, do you do this full time for Canonical? 

I wish.

>  I am amazed at how quickly you respond, as well as the sheer number of responses you have logged.  :)

I just so happened to log in at the time and knew the answer (or a lucky guess) and by the way, there are a few others who have more beans than I do.  They just decide not to show.  ;) 

> I am just starting with Kubuntu after happily using Xandros for the past 5 years.  I run Linux exclusively on 7 machines that I maintain at home and in my small business.  Xandros 4 has been a bit of a disappointment, however.  It was either Kubuntu or SuSE (I have both), and I have a preference for Debian-based rather than RPM distros, simply because of familiarity.

Frank.

I used to have SuSE on my machine but removed it a while back.  That baby is NOT going on my machines again.

---

