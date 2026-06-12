---
title: "Upgrading 9.10 to 10.04 beta."
date: 2010-04-21
forum: Installation &amp; Upgrades
---

### Post by chrispche on 2010-04-21
What would the terminal command be to upgrade my 9.10 Ubuntu Desktop to 10.04. I was told that it's pretty much stable now, so I would like to do a internet upgrade.

I'm running the amd64 version of Ubuntu 9.10 if that's any help.

Here is a copy of my sources:

[[img]http://i65.servimg.com/u/f65/11/95/68/21/source10.png[/img]](http://www.servimg.com/image_preview.php?i=29&u=11956821)

Can this be done?

Cheers.

PS I'm an impatient BLEEP. I want to try 10.04 now!

---

### Post by drs305 on 2010-04-21
The recommended command is:
```

sudo update-manager -d

```

You need the -d switch since Lucid is still Beta (think d=development).

Here is a link on upgrading:
[http://www.ubuntu.com/testing/lucid/alpha2]("http://www.ubuntu.com/testing/lucid/alpha2")

---

### Post by Mark Phelps on 2010-04-21
Maybe I'm telling you something you already know ... but upgrading to 10.04 is not really "trying" it; it's replacing what you have today with 10.04.  And if there are any major problems, there's no Linux equivalent of the MS System Restore to go back to what you had before.

If you really just want to try it, you would do better running from the LiveCD; that way, nothing will be changed until you confirm that everything works.

---

### Post by Jake007g on 2010-04-21
Press ALT+F2 whilst 9.10 is running, and then type:

> update-manager -d

Into the 'run' box, leaving all check boxes default. Click OK and proceed to upgrade.

It's always recommended to do a fresh install from a live-CD though.

---

### Post by chrispche on 2010-04-21
> **Mark Phelps said:**
> Maybe I'm telling you something you already know ... but upgrading to 10.04 is not really "trying" it; it's replacing what you have today with 10.04.  And if there are any major problems, there's no Linux equivalent of the MS System Restore to go back to what you had before.

If you really just want to try it, you would do better running from the LiveCD; that way, nothing will be changed until you confirm that everything works.

I know but. I have been told that for a beta, Lucid is very stable. Oh **** it I'll just wait.

---

### Post by lucasart on 2010-04-21
> **chrispche said:**
> I know but. I have been told that for a beta, Lucid is very stable. Oh **** it I'll just wait.

i dont know who told you that, but my experience of testing lucid is pretty disastrous. though bugs are being fixed as we speak and dont affect everyone the same way (depending on hardware compatibility etc)

---

### Post by chrispche on 2010-04-21
Well that was a failure. It complained about Openoffice. Not being to able to upgrade. Well, I am Buddhist and supposed to be patient I'll wait for the final version.

However, what I want to know is will I be able to upgrade with out problems then?

Little bit worrying that.

I really have a lovely working Ubuntu Linux and have everything as I want it. I even have a Virtualbox of Windows 7 and Windows XP fully configured. I really REALLY don't want to start over again.

When Lucid is finally released will I be able to upgrade without hick ups? Is the problem I'm having now, purely a beta situation?

Hmmmmmmmmmm.

---

### Post by chrispche on 2010-04-21
Anyone have any thoughts???

---

### Post by drs305 on 2010-04-21
> **chrispche said:**
> Anyone have any thoughts???

I haven't seen (m)any OO complaints on the Lucid upgrades. I suppose it's possible that you caught the repositories at a time when there were unmet dependencies - the same situation as when someone who already has Lucid tries to upgrade and is met with the "partial upgrade" message. 

Even if that were the case, it might just be better to wait for the final release unless you get that message very quickly on the upgrade attempt. I wouldn't recommend spending much time on the attempt between now and the official release.

---

### Post by chrispche on 2010-04-21
I take it your using 10.04, how do you find the stability?

---

### Post by kcreek33 on 2010-04-21
I have been using 10.04 and haven't had many problems so far.  The only issues I have had deal with the video drivers for my newer ATI HD 5770 card.  Other than that, it reported that the screensaver crashed after coming from hibernation mode, but didn't require a reboot or kill anything else.

Overall, seems pretty stable for me.

I should probably note that I did a fresh install.

---

### Post by chrispche on 2010-04-21
Tried again and this is the error I'm getting:

Error during commit
'E:Couldn't configure pre-depend openoffice.org-core for openoffice.org-filter-binfilter, probably a dependency cycle.'
Restoring original system state

Any idea's?

---

### Post by yogesh.girikumar on 2010-04-23
Hi,

You can fix this issue by un-installing the "openoffice.org-filter-binfilter" package.

Run the following in the terminal,

```
$ sudo apt-get remove openoffice.org-filter-binfilter
```

Then run the dist-upgrade again. Since most files would have already been downloaded, the installer won't attempt to download them again.

```
$ sudo apt-get -f dist-upgrade 
```

HTH,
Yogesh.

---

### Post by skbhat03 on 2010-04-23
Everything was working fine till few days back.
I had upgraded to 10.04 without any problem when it was Beta 1.

And later it was upgraded to Beta 2 automatically. But the problem started few days back.
I had around 200 updates waiting in update manager, i went a head and updated after that my laptop wont boot !.
Just the initial screen with "Ubuntu" log and there after a black screen.

Then i did a clean installation of Beta 2, worked fine, but again after update, same issue.

Now i tried to boot from a live CD RC1, but same issue again.

Any idea how i can fix it ?

---

