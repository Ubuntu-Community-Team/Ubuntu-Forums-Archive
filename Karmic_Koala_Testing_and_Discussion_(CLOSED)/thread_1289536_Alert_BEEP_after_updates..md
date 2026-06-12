---
title: "Alert BEEP after updates."
date: 2009-10-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by bpickel on 2009-10-12
I was wondering if anyone else had seen this issue. After one of the frequently occurring rounds of updates, I have noticed that instead of the Ubuntu drumroll sound I used to get for notifications it  is  now the loud and annoying system beep. 

  I can blacklist the pcspkr or more correctly snd_pcsp modules and that stops the sound but I am pretty sure Karmic was using the "drumroll" sound before.  Soooo, someone either tell me I am crazy or maybe ........HELP !

---

### Post by autocrosser on 2009-10-12
Was that after a update to ubuntu-sounds?  If so, you could look both in your System Sound panel & /user/sounds/ubuntu/stereo for it & change it to something more to your liking.

---

### Post by bpickel on 2009-10-12
I do recall seeing there was an update to ubuntu-sounds.

I will try and be a little more detailed. 

The sound I am hearing is the loud beep that you would get from the pc speaker not any sound that it is supposed to be. This, to me, is indicative of some thing going wrong and that being used as a fall back. Used to be the "drumroll"

I have changed the sounds in System > Preferences > Sounds to no avail ! 

If I look at the sounds in /usr/sounds/ubuntu/stereo they are there (only one set of sounds ?) and i can play all the files. The notifications at login work.  So here are some of the places I have this happening.

1.   If I am typing the password to authenticate a process (Update Manager) and hit backspace when there are no characters, I get the beep.

2. If the notification daemon notifies me of  a new email, I get the beep. 


I have already done the blacklist trick.   I have also created a new user for testing and the problem persist which would logically dictate that it is systemic.  

I have also reinstalled the ubuntu-sounds package, also with no luck.  I wonder if I am the only person who is seeing this.

---

### Post by Boondoklife on 2009-10-12
I have the same issue and damn if it isnt annoying!

---

### Post by bpickel on 2009-10-12
Well at least I know I am not going mad !    I will continue to plug away.

---

### Post by Boondoklife on 2009-10-12
You can disable the speaker in alsamixer, it is a dirty little bandaid to shut that thing up. Just use the right arrow to get to pc beep and press m then esc.

---

### Post by bpickel on 2009-10-12
Yeah that doesn't get it either.  It seems it's only when backspacing in a dialog and with the OSD notifications

---

### Post by starzinger on 2009-10-13
> **Boondoklife said:**
> You can disable the speaker in alsamixer, it is a dirty little bandaid to shut that thing up. Just use the right arrow to get to pc beep and press m then esc.

This worked for me, thanks.

---

### Post by Boondoklife on 2009-10-13
Hmm well i rebooted and to my surprise that dang thing is back on. looks like we need to save it and then restore it on boot.

get it setup just the way you like and then use `alsactl store` then fire up your editor and put alsactl restore in your /etc/rc.local file. that will set it for good.

---

### Post by bpickel on 2009-10-13
I happen to have an image of my hard drive from last Friday. I have restored and  I don't have the beep issue.  I am currently letting updates run and have excluded the Ubuntu sounds update I think is the culprit. I will post back as soon as up dates complete and let everyone know.

---

### Post by bpickel on 2009-10-13
So it would appear that it is not the ubuntu-sounds package.   Ran updates and problem is back !!  BEEP everytime I get an email or backspace too many time. Pc speaker is off in alsamixer still have the issue.   It's always something. Maybe a magic update will come to fix the issue !   Damned if I know how !


Edit.    Ok so after this post I installed the Ubuntu Sounds package I had left out and now the notifications beep when i get emails is cleared up but I have no alert sounds, If I go to System > Preferences > Sounds and try say....Bark, I get nothing ? So I think we just have some funkiness going on and will probably have to wait unless anyone can help.

---

### Post by bpickel on 2009-10-13
Unrefined = Yes 
Amateur = Yes 
Effective = Yes 

I made a little file issuing these commands 

xset b off
xset b 0 0 0 

You can run these in a terminal and see if that corrects the bell issues (if anyone is still following this thread).  If so,  take the attached file extract and place the "killbell" file somewhere safe, then make sure it is executable as a program, then add a startup application entry that points to this file and for the time being.....no bell !!! Tested in all of the areas that I referenced earlier. :guitar:

If you have the shutdown bell it is answered in other posts.

---

### Post by jdeslip on 2009-10-13
I too have this annoying problem after the recent update.  Has anyone filed a bug on launchpad?  Thanks for the workarounds, but getting it fixed for final would be ideal.

---

### Post by EMVirostek on 2009-10-13
I have to very same issue...only I'm in Mint Gloria.  I know it's basically Ubuntu, but I've had this issue since I made the switch from windows 2 weeks ago.

I did make one observation though...I unchecked the "audible bell" in the Compiz general tab and not only do I get that annoying beep when I get an email, but the visual alert kicks in and my screen gets all wavy.  To me, this sounds like something is wrong...not just an annoying sound issue.

---

### Post by bpickel on 2009-10-14
There is certainly something amiss.  I have not tried to see if compiz could be affecting things but I will. I was hoping this mornings round of updates would help us out but no love.....    This thing seems widespread.  We do need to get a bug report filed. 

I'll report back on compiz.....

---

### Post by skillllllz on 2009-10-14
I am having this problem too and it is very annoying. Is there anything I can do to help test/resolve this?

---

### Post by bpickel on 2009-10-15
See post 12 in this thread.  It is a temp fix but it will get rid of the beep. I keep hoping each update will bring relief as there doesn't seem to be much community movement or interest in a resolution here. Whatever it is, must be over my head, I cannot find it.

---

### Post by bpickel on 2009-10-15
So it would appear that this issue is corrected with the latest updates.  Can some confirm please and let know.

---

### Post by EMVirostek on 2009-10-15
here's an interesting question...

Since I'm running Mint (which is Ubuntu), do you think the ubuntu updates will reach me?

---

### Post by hvbakel on 2009-10-15
Yes, this is now fixed for me as well.

---

### Post by bpickel on 2009-10-15
> **EMVirostek said:**
> here's an interesting question...

Since I'm running Mint (which is Ubuntu), do you think the ubuntu updates will reach me?


I think that the fundamental updates should be in sync. But I not 100% certain.

---

### Post by bpickel on 2009-10-15
> **hvbakel said:**
> Yes, this is now fixed for me as well.

Good to hear ! After a few more folks confirm I will marked as solved.

---

### Post by bpickel on 2009-10-15
To the top (BUMP)

---

### Post by skillllllz on 2009-10-15
I just checked. I still have the annoying beep after all latest upgrades performed just now. I tried rebooting as well... it's still happening.

---

### Post by Junior_Sampa on 2009-10-15
> **skillllllz said:**
> I just checked. I still have the annoying beep after all latest upgrades performed just now. I tried rebooting as well... it's still happening.

Here is also the same even after all the updates.

Junior

---

### Post by jonathank89 on 2009-10-16
> **bpickel said:**
> Unrefined = Yes 
Amateur = Yes 
Effective = Yes 

I made a little file issuing these commands 

xset b off
xset b 0 0 0 

You can run these in a terminal and see if that corrects the bell issues (if anyone is still following this thread).  If so,  take the attached file extract and place the "killbell" file somewhere safe, then make sure it is executable as a program, then add a startup application entry that points to this file and for the time being.....no bell !!! Tested in all of the areas that I referenced earlier. :guitar:

If you have the shutdown bell it is answered in other posts.

I've made my own fix that basically does the same thing, but is a little less work.

Basically uses the alsamixer, it's very easy and works great!

Check it out: [link]("http://friendlytechninja.vndv.com/2009/10/16/howto-fix-alert-system-beep-in-ubuntu-9-10-karmic-koala/")

[http://friendlytechninja.vndv.com/2009/10/16/howto-fix-alert-system-beep-in-ubuntu-9-10-karmic-koala/](http://friendlytechninja.vndv.com/2009/10/16/howto-fix-alert-system-beep-in-ubuntu-9-10-karmic-koala/)

Just another option for people :)

Jonathan

---

### Post by bpickel on 2009-10-16
That's cool, it is fixed for me now.   I tried turning sounds off in alsamixer and I still had it !! Only the two commands got it for me.:(

---

### Post by Junior_Sampa on 2009-10-16
> **jonathank89 said:**
> I've made my own fix that basically does the same thing, but is a little less work.

Basically uses the alsamixer, it's very easy and works great!

Check it out: [link]("http://friendlytechninja.vndv.com/2009/10/16/howto-fix-alert-system-beep-in-ubuntu-9-10-karmic-koala/")

[http://friendlytechninja.vndv.com/2009/10/16/howto-fix-alert-system-beep-in-ubuntu-9-10-karmic-koala/](http://friendlytechninja.vndv.com/2009/10/16/howto-fix-alert-system-beep-in-ubuntu-9-10-karmic-koala/)

Just another option for people :)

Jonathan

Thank you Jonathan!! This finally worked for me! =D>

I also hope they correct this bug till the final release.

P.s. Your website looks like to be very interesting!

Congratulations!
Junior

---

### Post by Alfaspyke on 2009-10-17
Hmm.

You guys report that if you blacklist the pcspkr module, and remove the module manually, you get rid of this problem.
On my laptop (Dell preciision m4400) the problem is completely opposite.
The system is updated as of today. Oct.17.

The pcspkr module was not loaded by default.

I had a terrible LOUD Buzzing sound whenever the system bell should have sounded.
For example when I pressed TAB in a bash session to get autocompletion.
Or backspace when there is no characters to delete.

No adjustments in the sound preferences in Gnome had any impact.

I also could not rmmod the pcspkr module as suggested in this and many other threads.
This was normal as the module was not loaded in the first place.

So out of desperation I loaded it manually.
OH HEAVENLY BLISS!!! Silence!!! :-)

Even the systembell settings in the sound preferences works now.
Bark, drip, glass and so on.
And by work I mean that the actual sound is played as a preview when I click them.
When the pcspkr module was NOT loaded there was no sound from the preview in sound preferences....

I can not explain this as this is WAY beyond my expertise.

The system "ding" in a terminal session (bash - autocompletion) is silent at the moment, but compared to the alternative this is progress.

Just letting you guys know my experience on the problem

---

### Post by jonathank89 on 2009-10-17
Did using my method not work for you?

Using the alsamixer to mute the system speaker?

[Link to fix]("http://friendlytechninja.vndv.com/2009/10/16/howto-fix-alert-system-beep-in-ubuntu-9-10-karmic-koala/")

---

### Post by Alfaspyke on 2009-10-17
Muting the PC speaker using alsamixer did indeed work.
But after modprobing the pcspkr module I dont have to mute that audio channel anymore.

---

### Post by skillllllz on 2009-10-22
Okay, this is really strange. I still have this issue with the alert beep. I, much like another user in this thread, noticed that the pcspkr module is not being loaded automatically. So, I opened a gnome-terminal window and entered the command: sudo modprobe pcspkr. PRESTO! The aleart beep stoped and everything functioned as it should.

I then assumed the next and proper thing to do was force it to load the pcspkr module on boot, so I  added a line to /etc/modules for that. What happens now makes little sense; the module loads but the alert beep returns. If I unload it and then load it again via the gnome-terminal, the beep disapears.

Can someone help me understand how or why this would happen? What is the difference between loading a module on boot versus manually from the terminal. The only thing I can think of is the order the modules are loaded, but I know little about that right now.

---

