---
title: "Synaptic / apt-get broken packages problem (?)"
date: 2013-08-31
forum: Installation &amp; Upgrades
---

### Post by sawbona on 2013-08-31
Good morning:

I'm a reincident/persistent linux user, having tried many times to move from the MS platform with little success.
So to all extents and purposes I can say that I'm sort of new(ish) to linux.

I'm now giving Ubuntu 12.04 LTS a try.

I started by installing 10.04 and then doing an online upgrade to 12.04 LTS.

I have been attempting to get the infamous ath9k_htc driver problems fixed and the Matrox G400 twin head card properly configurated but I have not had much success save being able to narrow the ath9k_htc driver problems to something related to CRDA configuration data in the adaptor's EEPROM and how 12.04 LTS deals with it.

I've installed Synaptic Package Manager (absent from 12.04 LTS) and used it to install and upgrade the system.
I've also installed deborphan.

The question at hand is this:

If I run Synaptic Package Manager, select the 'custom filter' tab and then the 'broken' package list, I see that Synaptic says: 

---
1683 packages listed, 1683 installed, 0 broken, 0 to install/upgrade, 0 to remove.
---

According to the help file, the procedure is this:

---
To show all broken packages choose the Broken filter.

To correct the broken packages perform the following steps: 

Choose Edit &#9656; Fix Broken Packages from the menu.

Apply the marked changes to actually fix the packages:

Click on Apply in the toolbar.

Choose Edit &#9656; Apply Marked Changes from the menu.

Press the key combination Ctrl+E.
---

But when I do --> Choose Edit &#9656; Fix Broken Packages from the menu the 'Apply' button remains shaded and cannot be clicked on.

```
 --> sudo apt-get upgrade

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

--> sudo apt-get install -f

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

sudo apt-get clean && sudo apt-get update

--> sudo apt-get install --fix-broken
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Why are 1683 packages listed as broken?
Am I missing something here?

Thanks in advance,

CIV

---

### Post by ibjsb4 on 2013-08-31
I don't know why synaptic is showing 1600+ packages and 0 broke.  Install -f is showing 0 packages broke.

> I started by installing 10.04 and then doing an online upgrade to 12.04 LTS.

You should really do a reinstall of 12.04 fresh from the CD.  By installing and upgrading your out of date 10.04 install you are off to a bad start IMO.  10.04 runs on gnome2 and 12.04 uses the new gnome3.  Upgrades can go smooth or cause headaches.

---

### Post by Dennis N on 2013-08-31
> **sawbona said:**
> 

Why are 1683 packages listed as broken?
Am I missing something here?

Thanks in advance,

CIV

> 1683 packages listed, 1683 installed, 0 broken, 0 to install/upgrade, 0 to remove
1683 is the total number of packages installed, not the number broken. 0 (zero) is the number broken.

Edit: I see your point. I did the broken filter on mine and get:

**0 packages listed, 1539 installed, 0 broken, 0 to install/upgrade 0 to remove.**

Is the Synaptic window empty after using the filter? Mine is.

Possibly some artifact from your upgrade is causing this. Consider complete removal and reinstall of Synatptic, or as suggested above, a fresh install if that fails. Or live with it as is.

---

### Post by ibjsb4 on 2013-08-31
> **Dennis N said:**
> 1683 is the total number of packages installed, not the number broken. 0 (zero) is the number broken.

Correct, but ..

[ATTACH=CONFIG]245865[/ATTACH]

Is the way it should read

---

### Post by sawbona on 2013-08-31
Hello:

Thanks for your input.
I'm sorry, the original install was 11.10 and not 11.04.
My bad ...

>  You should really do a reinstall of 12.04 fresh from the CD 
Hmmm ...
That sounds 'very' MS like ...    I 'was' hoping that with linux it would now be part of a distant past.
Maybe not? =-P

Seriously, I did my best but 12.04 LTS would not install no matter what I tried, for days on end.
So I decided on 11.10 which I (initially) had no intention of upgrading.

But in the end, thinking that 'maybe' the Xorg.conf problem would have been fixed, I updated to 12.04 LTS.
But (as it has been for the longest time) the Xorg.conf problem has 'not' been fixed.   =-/
Yet.

Cheers,

CIV

---

### Post by sawbona on 2013-08-31
Hello:

Thanks for your input.

> 
1683 is the total number of packages installed, not the number broken. 0 (zero) is the number broken.

Hmmm ...

If I look under 'Sections --> All',  SPM tells me that the system has 39763 packages listed, 1683 installed, 0 broken, 0 to remove.  
If I look under 'Custom filters' --> 'Broken' SPM tells me that the system has 1683 packages listed, 1683 installed, 0 broken, 0 to remove.

I think that it being the 'Broken' filter, if there are 1683 'listed', it would mean that there are 1683 'broken' packages.
If this is so, there's a discrepancy between the 'listed' packages (1683) and '0 broken'.

> 
I see your point. I did the broken filter on mine and get:
**0 packages listed, 1539 installed, 0 broken, 0 to install/upgrade 0 to remove.**


Exactly ...

> Is the Synaptic window empty after using the filter?
No ...

Like I wrote in my OP, there's a long liste which I'm willing to  bet counts up to 1683.

> 
Possibly some artifact from your upgrade is causing this.

Could be ...
In any case, it was an upgrade from 11.10 and not from 10.04, corrected above.

> 
Consider complete removal and reinstall of Synatptic.


I'll try that one.

Thanks.

CIV

---

### Post by sawbona on 2013-08-31
Hello:

Thanks for your input.

> 
Is the way it should read


Thought so ...

This is what my screen looks like:

[ATTACH=CONFIG]245868[/ATTACH]

[U]ADDITIONAL INFORMATION
[/U]
I did as sugegsted above and did a complete removal of SPM, rebooted and:

```


--> sudo apt-get upgrade
--> sudo apt-get install -f
--> sudo apt-get install --fix-broken


```

Then:

```


--> sudo apt-get install synaptic


```
Unfortunately, the situation has not changed at all.
Same thing reported by SPM.

What I did find interesting/strange was that in the course of removing SPM (using SPM, of course) I noticed that the number of packages listed by SPM as 'broken' was suddenly reduced to five or six packages. The application dissapeared from screen as I intended to delve further.

Could it be that SMP 'itself' is breaking the packages that dissapeared or something SPM needs is missing?

I have no idea what to do now.

Any firther input will be appreciated.

Thanks in advance.

CIV

---

### Post by ibjsb4 on 2013-08-31
Open SPM in terminal and see if it gives any errors

```
gksudo synaptic
```

---

### Post by sawbona on 2013-08-31
Hello:

Thanks for your input.

> Open SPM in terminal and see if it gives any errors

Same behaviour.
Just opens up SPM GUI.

Cheers,

CIV

---

### Post by bapoumba on 2013-08-31
I may not read correctly here, but both apt-get and synaptic report 0 broken packages. So there may be just an error in the number of packages listed in the broken filter or some left overs from your upgrade. Just a guess. I had a quick look around synaptic to see where this number comes from but did not find anything real relevant. 

Please try ```
sudo apt-get clean
sudo apt-get autoremove
```

I would not worry too much, unless a real broken package shows up in apt-get.

---

### Post by sawbona on 2013-08-31
Hello:

Thanks for your input.

> 
... but both apt-get and synaptic report 0  broken packages.

You read right.
The thing is that SPM lists 1683 in the 'Broken' filter screen.
Should be none listed there.  (?) (see the screenshot)

 > 
... may be just an error in the number of packages  listed in the broken filter ...

Could be.

The thing is that after a complete removal of SPM and reinstallation, the list survived.
Shouldn't it have been done away with?

> 
 ... left overs from your upgrade. Just a  guess.

Could be ...

But then it could be something else.
Re: 
 
> What I did find interesting/strange was that in the course of removing  SPM (using SPM, of course) I noticed that the number of packages listed  by SPM as 'broken' was suddenly reduced to five or six packages. The  application dissapeared from screen as I intended to delve further.


Makes me wonder ...

Cheers,

CIV

---

### Post by bapoumba on 2013-08-31
Yes, I agree it looks curious. Have you tried the housekeeping (clean & autoremove) ?

---

### Post by hg-knight on 2013-08-31
as above, or Synaptic does a great job of fixing broken packages

---

### Post by bapoumba on 2013-08-31
OK, something close to what I was looking for. Maybe some config file :
[http://ubuntuforums.org/showthread.php?t=1976309](http://ubuntuforums.org/showthread.php?t=1976309)

---

### Post by sawbona on 2013-08-31
Hello:

Thanks for your input.

> 
Have you tried the housekeeping (clean & autoremove) ?


Yes, I did.
There was nothing to clean or remove.

Still looking ...

Cheers,

CIV

---

### Post by sawbona on 2013-08-31
Hello:

> 
OK, something close to what I was looking for. Maybe some config file :


I'll check it out and post when I get back home.

Thanks for the link.   =-)

Cheers,

CIV

---

### Post by bapoumba on 2013-09-01
Sure, it may not be that exact config file, but one in the same folder.

---

### Post by sawbona on 2013-09-02
Good morning:

First of all, thanks a lot to all who replied.
Second, good news: it was much ado about nothing.

So, just 'why' did the 'broken' filter list 1683 packages files while at the same time telling me that there were no broken files?
And with 1683 being the exact number of 'installed' files?

Well ...
The answer is quite simple: because it SPM was configured to do exactly that.

Settings --> Filters --> Broken --> Current had the 'Installed' box ticked.

I'm sure it is not a default setting and since I'm the only one playing with it, the 'reason' for the box being ticked is quite evident.  =-/

So ...
 SPM works as intended and this was intended behaviour.

Cheers,

CIV

---

### Post by bapoumba on 2013-09-02
Oh cool, I was kind of scratching my head to be honest. Did not think about that, thanks :)

---

