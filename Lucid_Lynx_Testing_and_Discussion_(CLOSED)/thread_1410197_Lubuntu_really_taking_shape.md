---
title: "Lubuntu really taking shape"
date: 2010-02-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by rogerdean on 2010-02-18
Hello all

I just gave the upcoming Lubuntu a run, and have to say it's looking really very nice. I have no stats, but it is clearly so much snappier than Ubuntu or Xubuntu - that's what it's for after all...

A lot of application choices and artwork landed in the updates of the last few days, giving you the screenshot attached. Don't judge it on what you get just from the alpha2 image - do the updates through synaptic (no update manager yet). Chromium is the browser, and I guess Firefox won't be in the next alpha

All the download links etc are here
[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

Cheers
Roger

---

### Post by ranch hand on 2010-02-18
Lubuntu really is nice.  I have a nice fast machine but I like Lubuntu a lot.

They are hoping to get pcmanfm2 out in time for the release.

---

### Post by seeker5528 on 2010-02-18
I think I liked the wallpaper with the LXDE logo a little better, but the new wallpaper is nice.

I like the icon theme and panel graphic better than what was being used.

I just installed the lubuntu-plymouth-theme and have a nice looking graphic during boot up now.

Now if I could just figure out what to use to handle USB media (flash drives, external HDDs, etc...) I could see this being my primary environment. Seems a little broken in Ubuntu prime anyway at the moment, at least for me. 

Later, Seeker

---

### Post by VMC on 2010-02-18
This a really good new. I didn't like Xubuntu very much. I followed Lubuntu from the start, but it seemed like it was stalled. Now perhaps it will take off. I'll try that link again.

Thanks for the update.

---

### Post by phillw on 2010-02-19
Indeed it is looking good, popped it onto my usb drive that held the 'rc' of Ubuntu 10.04 & booted with it - a stream of error messages at boot, but boots okay - it is fast :-)  Just updated to firefox 3.6 Very impressed.  Phill.

---

### Post by forcecore on 2010-02-19
is there somewhere daily builds of Lubuntu 10.04?

---

### Post by ronacc on 2010-02-19
burned lubuntu to a usbstick using unetbootin , like phillw I got a string of error msgs during boot but it went to desktop ok , I think the errors are related to unetbootin and also lubuntu looking for the cd it isn't on . I'll try it later on my EEE 701 , it just might become my default for that.

---

### Post by ranch hand on 2010-02-19
> **forcecore said:**
> is there somewhere daily builds of Lubuntu 10.04?
No there is not.

This is a very small, independent team.  They do not have the resources for doing a build daily.

I would watch the wiki and see when A3 comes out (it may be a little later than Ubuntu).

---

### Post by Ibidem on 2010-02-19
Nice to here this.
I've got a system that runs pcmanfm on icewm, and I might add some more LXDE stuff.
But if you're wondering about usb drives, what I did was install usbmount and then tweak it-
[see here]("http://ubuntuforums.org/showpost.php?p=8848654&postcount=6") for what I did.

Ibidem

---

### Post by forcecore on 2010-02-19
quite interesting lightweight desktop, Lubuntu should add disk utility because it is most unique software for formatting and powering down disks physically.

---

### Post by ranch hand on 2010-02-19
> **forcecore said:**
> quite interesting lightweight desktop, Lubuntu should add disk utility because it is most unique software for formatting and powering down disks physically.
Join the mailing list and testing team and suggest that.

I am going to suggest that later today and, if I can make it, on the IRQ meeting Sunday.

---

### Post by gilir on 2010-02-19
> **ranch hand said:**
> 
I am going to suggest that later today and, if I can make it, on the IRQ meeting Sunday.

The meeting is on Saturday finally, in #lubuntu on freenode.

---

### Post by ranch hand on 2010-02-19
I better check my mailing list more often.  Thanks a bunch.

Hope I can make it.  Have firewood to stack that I cut today and a cord coming in for the dreaded mother in law that day too.

---

### Post by phillw on 2010-02-19
> **ronacc said:**
> burned lubuntu to a usbstick using unetbootin , like phillw I got a string of error msgs during boot but it went to desktop ok , I think the errors are related to unetbootin and also lubuntu looking for the cd it isn't on . I'll try it later on my EEE 701 , it just might become my default for that.

I tracked them down to /var/log/casper.log - Looking for /dev/sr0 and not finding it. Looks like a glitch in persistance.

I had some fun updating FireFox to 3.6 and sorting out Flash support - It went and got Chromium. I must say, I'm quite impressed with Chromium - Took my bookmarks over from FFox and I've been told it is less RAM hungry than FFox, which is important for Lubuntu.

Re:EEE 701

> This machine is a 500MHz PIII with 640MB RAM and runs quite smoothly.

My other test machine is a 266MHz PII with 129MB 66Mhz RAM and struggles a bit if you have music playing , a browser open , mail client and xchat running.


"*Struggles a bit*" ? - How about report itself to the national league for cruelty against computers ? ;)

Phill.

---

### Post by zeroandone on 2010-02-20
Lubuntu looks good. But I just tried the LiveCD and haven't installed it. Does it support Ubuntu One? Anyone installed Wine in Lubuntu?

---

### Post by ranch hand on 2010-02-20
Lubuntu 10.04 is based on Ubuntu 10.04.  Therefore anything in the repos should be supported.  If not let them know.

The idea is to have Lubuntu as light as possible and to support older hardware so the initial install is small.  I added a bunch of stuff that I like.

Ubuntu One does not interest me at all but I am sure it will work without a problem.  Most of the dependencies should be there I think.

I have no idea about wine, won't have it on my box.  I do not see any reason why it would not work though.  May work better on a light system.

---

### Post by phillw on 2010-02-20
> **ranch hand said:**
> I better check my mailing list more often.  Thanks a bunch.

Hope I can make it.  Have firewood to stack that I cut today and a cord coming in for the dreaded mother in law that day too.

I've posted the log of the IRC onto the wiki page, but it's not working correctly. -- Okay, so I'm a complete n00b at such things ;-)

I did ask the question posed here on the chat and there was a discussion about it. While I await someone to explain to me where I went wrong on my popping it onto the wiki page - I've gone put it on my baby forum --> [http://forum.phillw.net/viewtopic.php?f=4&t=41](http://forum.phillw.net/viewtopic.php?f=4&t=41)

It **is** where it should be --> [https://wiki.ubuntu.com/Lubuntu/IRC%20Meetings](https://wiki.ubuntu.com/Lubuntu/IRC%20Meetings)   Just not working correctly.  :confused:

Regards,

Phill.

---

### Post by rogerdean on 2010-02-26
There's an alpha3 out...
[http://lubuntu.net/](http://lubuntu.net/)

---

### Post by phillw on 2010-02-26
> **rogerdean said:**
> There's an alpha3 out...
[http://lubuntu.net/](http://lubuntu.net/)

I'm using it, please give the PCMan File Manager a good shake down for the author :D

Phill.

---

### Post by rogerdean on 2010-02-26
hmmm... it gave me pcmanfm 0.9 - is this right? also, phil, do you know where i should report bugs? the launchpad page is so empty i think it can't be the right place
cheers

---

### Post by rogerdean on 2010-02-26
ah, bugs go to [email]lubuntu-desktop@lists.launchpad.net[/email]

---

### Post by rixtr66 on 2010-02-26
im giving lubuntu a test run.i have to say im impressed so far!
its very fast.i will be testing audio production on it just like 
lucid lynx.so ill be trying to push lubuntu!
Rick :guitar:

---

### Post by haydoni on 2010-02-28
Upon installing Ubuntu to my GFs 6-year-old laptop, it kept crashing - on boot/randomly - presumably for want of CPU/ram... so lubuntu seemed like a good choice, I'm very impressed with it:

WINE seems to be working in Lubuntu. However, contrary to previous Ubuntu releases (and similarly to Ubuntu LL??) you need to make .EXEs executable (chmod 755 them in terminal).
I now have spotify running perfectly on my GF's old laptop.

I'm not sure about Ubuntu One - my quick look failed to notice it anywhere, I'll have another look later today; She'll really want this as she's had two hard-drives die on her already.


One annoyance - you can't change the number of panels (to one) through the panel interface - it's uneditable. When using the touch-pad, I seem to regularly accidentally scroll away for the panel I was in! And then I have to sensitively scroll an odd number of units back to it (trickier than it sounds). I'd prefer to only have the one panel.

Oh and another, looking at hardware drivers, it told me the wireless one I wanted - great! I clicked on it - you don't have permission to install this driver - (not asking for a password) oh! I installed through Synaptic no problemo (made easy as I knew, from hardware drivers, exactly the driver I needed:))


The current and only issue left is of flash (in 4od) jumping quite a bit... Hopefully I'll fix that today.

---

### Post by ranch hand on 2010-02-28
They are not including a lot of things in Lubuntu to keep the size down.

Ubuntu One is available in synaptic.

---

### Post by haydoni on 2010-02-28
For Ubuntu One: I followed instructions [here]("https://one.ubuntu.com/support/installation/"). However, Step 3. Ubuntu One is in preferences rather than Internet Applications.

It works through the browser (did this happen already?) but files aren't automatically updated by placing files into the Ubuntu One folder (in home): as they do in Ubuntu LL.

---

### Post by haydoni on 2010-02-28
> **ranch hand said:**
> They are not including a lot of things in Lubuntu to keep the size down.

Ubuntu One is available in synaptic.

But unlike WINE, after installing via Synaptic, Ubuntu One is not really working.
Unless there something I'm missing...

---

### Post by ranch hand on 2010-02-28
I do not use Ubuntu One as I am a grumpy geezer who is paranoid about "cloud" computing (external drives are not expensive) so I am not the best to advise you but I believe you do need an account with them for that to work.

---

### Post by plun on 2010-02-28
I have severe trouble with both a Lubuntu and a LXDE session.

After login it just popups something on desktop in small squares....impossible to do something.

Where can I look for logfiles ?

---

### Post by haydoni on 2010-02-28
> **ranch hand said:**
> I do not use Ubuntu One as I am a grumpy geezer who is paranoid about "cloud" computing (external drives are not expensive) so I am not the best to advise you but I believe you do need an account with them for that to work. That's fair enough, however: I'm recklessly unparanoid. Yeah you need an account and I have it all working in Ubuntu LL - I really like it.

It has the very useful feature that you just drag and drop files into your /home/Ubuntu\ One folder and they are automatically backed up - in "the cloud". Rather than having to upload each file to the website manually via a browser.

In lubuntu I can't get this feature, automatically backing up files placed in Ubuntu One directory, doesn't "just work" (after following the instructions I linked to above).
However I can upload stuff via a browser...

---

### Post by ranch hand on 2010-02-28
Under Ubuntu you are using FF and in Lubuntu you are using Chrome (default browser in A3).   I wonder if that make a difference.

You are,  I think from my quick skim of the link, installing through FF in Ubuntu.  This may be what gives you the auto feature.

You may want to try it again with FF as your default browser.

---

### Post by haydoni on 2010-02-28
That's a good idea - but my default browser is chrome in Ubuntu, however there could well be some FF dependencies... I'll try installing FF and then reinstalling Ubuntu One.


HOWEVER, I've just noticed lubuntu isn't reading my USB sticks! The light goes on, but nothing in /media, /mnt or on the left hand side of file viewer... uh oh!

---

