---
title: "ubuntu jaunty alpha 1 test"
date: 2008-12-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by markg48 on 2008-12-08
downloaded jaunty alpha 1 today going to give it a whirl
havnt seen any real changes though

---

### Post by w3rt on 2008-12-08
> **markg48 said:**
> downloaded jaunty alpha 1 today going to give it a whirl
havnt seen any real changes though

No its pretty much still intrepid, the next alpha release will probably see more changes

---

### Post by markg48 on 2008-12-08
when alpha 2 comes out will i be able to install inside ubuntu or will i have to do another complete install

---

### Post by inobe on 2008-12-08
i would test it via virtual box or vmware, or even if you have a spare hard drive' bios boot..........

---

### Post by markg48 on 2008-12-08
dont need to jaunty runs perfect no errors or bugs so far

---

### Post by Slug71 on 2008-12-08
> **markg48 said:**
> when alpha 2 comes out will i be able to install inside ubuntu or will i have to do another complete install

As long as you keep up with the Updates you will have Alpha 2.

And yes its pretty much Intrepid with the 2.6.28 Kernel right now and Firefox 3.1 is also available in the repos.

---

### Post by ronacc on 2008-12-09
> **markg48 said:**
> dont need to jaunty runs perfect no errors or bugs so far

you should only use jaunty or any alpha or beta as a second install and have a stable install to fall back on , IT WILL BREAK .

---

### Post by Triggerhapp on 2008-12-09
> **ronacc said:**
> you should only use jaunty or any alpha or beta as a second install and have a stable install to fall back on , IT WILL BREAK .

When? :D
Mines stayed stupidly stable so far ;)

---

### Post by Eclipse. on 2008-12-09
> **markg48 said:**
> downloaded jaunty alpha 1 today going to give it a whirl
havnt seen any real changes though

The real changes are under the hood.

---

### Post by jerrylamos on 2008-12-09
> **Slug71 said:**
> As long as you keep up with the Updates you will have Alpha 2.

And yes its pretty much Intrepid with the 2.6.28 Kernel right now and Firefox 3.1 is also available in the repos.

UPDATES ABSOLUTELY KILLED ME!  I was running Jaunty via changing intrepid to jaunty in sources.list and then doing upgrade.  Ran O.K. for quite a few days updates then the UPDATES KILLED two of my four test pc's - those with Intel VGA (Intel, must be a small unknown company).  First sound died.  Updated some more and video died.

Finally the Daily Build went on a diet enough to squeak just under 700 mb.
CD Live worked, The CD Live ran where the updates didn't.  The four pc's are dual booted, installed daily build download 20081206 on all four.  Compaq sound runs on CD Live but not installed ?! bug #306387

On Intrepid I got killed on updates on my IBM Thinkpad.  Finally switched to daily build - if CD Live worked, O.K. install it, if it didn't. DON'T UPDATE.  And always dual boot so you have something to fall back on and also the 2nd install can be used to investigate messages and logs on the failed install.

My opinion anyewy, yours may vary.....Jerry

---

### Post by Eclipse. on 2008-12-09
> **jerrylamos said:**
> UPDATES ABSOLUTELY KILLED ME!  I was running Jaunty via changing intrepid to jaunty in sources.list and then doing upgrade.  Ran O.K. for quite a few days updates then the UPDATES KILLED two of my four test pc's - those with Intel VGA (Intel, must be a small unknown company).  First sound died.  Updated some more and video died.

Finally the Daily Build went on a diet enough to squeak just under 700 mb.
CD Live worked, The CD Live ran where the updates didn't. The four pc's are dual booted, installed daily build download 20081206 on all four. Compaq sound runs on CD Live but not installed ?! bug #306387

On Intrepid I got killed on updates on my IBM Thinkpad. Finally switched to daily build - if CD Live worked, O.K. install it, if it didn't. DON'T UPDATE. And always dual boot so you have something to fall back on and also the 2nd install can be used to investigate messages and logs on the failed install.

My opinion anyewy, yours may vary.....Jerry


Not updating your machine total defeats the point of using a development release, in Jaunty things change all the time (and it will be that way for the next few months.Telling users not to update their system to the latest packages is wrong.

Just file bugs on your problems and try and get them fixed.

Ps..My display hasnt broken yet and thats from before alpha 1 was released.

---

### Post by ronacc on 2008-12-09
> **Eclipse. said:**
> Not updating your machine total defeats the point of using a development release, in Jaunty things change all the time (and it will be that way for the next few months.Telling users not to update their system to the latest packages is wrong.

Just file bugs on your problems and try and get them fixed.

Ps..My display hasnt broken yet and thats from before alpha 1 was released.

He's not telling people not to update he's warning them to be careful! and how is installing a daily build "not testing" ? Just because jaunty has not broken yet for you does not mean no one has had major problems . caution is always the best policy with alphas and his (and my ) advice about a fallback is essential , how can you file bugs if you can't even boot ?

---

### Post by ShirishAg75 on 2008-12-09
> **jerrylamos said:**
> UPDATES ABSOLUTELY KILLED ME!  I was running Jaunty via changing intrepid to jaunty in sources.list and then doing upgrade.  Ran O.K. for quite a few days updates then the UPDATES KILLED two of my four test pc's - those with Intel VGA (Intel, must be a small unknown company).  First sound died.  Updated some more and video died.

Finally the Daily Build went on a diet enough to squeak just under 700 mb.
CD Live worked, The CD Live ran where the updates didn't.  The four pc's are dual booted, installed daily build download 20081206 on all four.  Compaq sound runs on CD Live but not installed ?! bug #306387

On Intrepid I got killed on updates on my IBM Thinkpad.  Finally switched to daily build - if CD Live worked, O.K. install it, if it didn't. DON'T UPDATE.  And always dual boot so you have something to fall back on and also the 2nd install can be used to investigate messages and logs on the failed install.

My opinion anyewy, yours may vary.....Jerry

Jerry if you still have the intel issue, please post your lspci -vvnn as well as your .xsession-errors as well as your xorg.log. I have put my bug at [lpbug]304871[/lpbug] . Have a look at the same and see if you have the same issue.

---

### Post by Eclipse. on 2008-12-09
> **ronacc said:**
> He's not telling people not to update he's warning them to be careful! and how is installing a daily build "not testing" ? 

I never said testing daily builds is wrong, I said telling users that their best not updating their systems is wrong, opposed to doing nothing.

> Just because jaunty has not broken yet for you does not mean no one has had major problems . caution is always the best policy with alphas and his (and my ) advice about a fallback is essential

Lots of things are broken, I just said my display was fine.I wasnt trying to making any sort of point. 

> how can you file bugs if you can't even boot ?

Note all the big warnings saying dont install Jaunty on a production machine!

---

### Post by computerfreak on 2008-12-10
so you can't ue jaunty alpha 1 in virtual box?

---

### Post by Eclipse. on 2008-12-10
> **computerfreak said:**
> so you can't ue jaunty alpha 1 in virtual box?

Yes you can.Just like you would intrepid or anything else.

---

### Post by rbmorse on 2008-12-10
> **Triggerhapp said:**
> When? :D
Mines stayed stupidly stable so far ;)

Give 'em a chance. They're still trying to figure out what they're really going to do with 9.04. 

When they come back from UDS they'll have some insanely great ideas about how to break the Jackalope.

---

