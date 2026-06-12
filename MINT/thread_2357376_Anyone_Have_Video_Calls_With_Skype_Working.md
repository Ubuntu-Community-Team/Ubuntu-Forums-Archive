---
title: "Anyone Have Video Calls With Skype Working?"
date: 2017-04-01
forum: MINT
---

### Post by tinker123 on 2017-04-01
Linux Mint 17 Qianna Cinnamon
Logitech C270 Desktop or Laptop Webcam


Hi,

I'm having trouble getting started with Skype and Mint.  I know this is an Ubuntu forum, but after doing Google searches ( and posting at Skype ) I got no answers.

I'm wondering if Linux users can make video calls with Skype at all.

I installed Cheese and that made videos of yours truly with zero problem so it doesn't seem like my webcam is the problem.

I tried the web based Skype in the latest, greatest, Firefox and Chromium.

I also tried the client app from the repo, Skype For Linux 4.3.

I also tried the client app for Linux, downloaded from the Skype site, Skype For Linux Beta Version 5.0.05

In all cases the camera icon was grayed out.

No error message, I can see and hear the person on the other end, but they can't see or hear me.

The only thing I did for "installing" the web cam was to plug it into a USB port.

Do I need to do anything else?

Thanks for any clues

Steve

---

### Post by howefield on 2017-04-01
Thread moved to the "*MINT*" forum.

---

### Post by Bucky Ball on 2017-04-01
I've never had a problem with video in Skype, but using Xubuntu so beside the point.

What I can suggest though is that you check the camera in something other than Skype, say 'Cheese' (should be in the repositories). You have given no details as to whether you have done this or not. Install Cheese, launch it and see if the camera works there. If not, then you can presume that the camera not working in Skype has nothing to do with Skype, but has to do with the fact your camera is not being seen by the system and is not working anywhere. 

That will position the goal posts and give you somewhere more definite to start diggging. ;)

I'm also not familiar with the cameras, but if USB, plug one in, immediately open a terminal and run

```
dmesg
```

What do you see at the bottom of that output? Does it look like it recognised and configured the camera (installed or loaded a driver)?

---

### Post by kostkon on 2017-04-01
Are you using the old Qt-based one from the repos or the new beta?

---

### Post by ajgreeny on 2017-04-01
Which version of skype are you using?
The repository version 4.3.0.37, still available in the canonical-partner repos should work fine with video in Mint, as it does in my Xubuntu 16.04, but if you have the beta version of Skype for Linux, which is all that was available originally, it does not support video, and you may need to get the new version which suggests it should have video calling from [https://www.skype.com/en/download-skype/skype-for-computer/](https://www.skype.com/en/download-skype/skype-for-computer/) though I have not yet tried this version.

This is available for 64bit systems only so if you have 32bit Mint you may be unlucky with this new skype for linux, though the repository version may still be available.

---

### Post by tinker123 on 2017-04-02
> **Bucky Ball said:**
> 

I'm also not familiar with the cameras, but if USB, plug one in, immediately open a terminal and run

```
dmesg
```

What do you see at the bottom of that output? Does it look like it recognised and configured the camera (installed or loaded a driver)?

**I see this:**


```

[175435.996072] usb 2-3: new high-speed USB device number 8 using ehci-pci
[175436.344662] usb 2-3: New USB device found, idVendor=046d, idProduct=0825
[175436.344668] usb 2-3: New USB device strings: Mfr=0, Product=0, SerialNumber=2
[175436.344672] usb 2-3: SerialNumber: C2D0FD00
[175436.344965] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0825)
[175436.434963] input: UVC Camera (046d:0825) as /devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3:1.0/input/input16
[175436.466533] set resolution quirk: cval->res = 384
Mint17QianaCinnamonBIOSF10$ 

```


> **Bucky Ball said:**
> 
Install Cheese, launch it and see if the camera works there.


Good suggestion.

Camera works great with Cheese.   Cheese came right up with a video of men looking into my screen :)

I also got Google Hangouts to work with camera with no problems.   Not in Firefox though it worked in Chromium.  

The online version of Skype didn't work in Chromium either.  When I hovered over the camera icon I got an icon of a hand with a crossed out circle.

---

### Post by tinker123 on 2017-04-02
> **kostkon said:**
> Are you using the old Qt-based one from the repos or the new beta?

I tried the web based Skype in the latest, greatest, Firefox and Chromium.

I also tried the client app from the repo, Skype For Linux 4.3.

I also tried the client app for Linux, downloaded from the Skype site, Skype For Linux Beta Version 5.0.05

---

### Post by Bucky Ball on 2017-04-02
You've probably been there, but open Skype from the repos (4.3 as I know this works with vid as using it myself), click 'Skype' on the toolbar, 'Options> Video Devices'. Your camera is connected there and selectable?

Just another suggestion: only have one camera plugged in at a time when trying this. Otherwise may create unecessary confusion. The one that is working with everything else best as you know that's working.

---

### Post by gordintoronto on 2017-04-03
Skype video calls used to work perfectly for me. However, the new Skype for Linux Beta appears to not support video. Cheese still works.

---

### Post by ajgreeny on 2017-04-03
Certainly the original skype-for-linux did not enable video, and the camera icon was always greyed out in the window. That is no longer the case, even though the version of skype still appears to be 5.0.0.5 for the version I downloaded April 1st.

The .deb package file I downloaded has an md5sum of **ac0c07a5b285a22ef0414dd5cd33d13f** so if yours is different from that perhaps you still have the older version of the .deb package.

---

### Post by ajgreeny on 2017-04-04
I think I have to eat humble-pie about this new skype-for-linux, which I have installed, as I said, but which after several attempts to get working properly seems to be giving me a lot of problems, whilst the original, and now presumably unsupported version 4.3.0.37 from the partner repos still seems to work with no problems. Users who are shown as online and I can contact with the old version are not showing in the new beta version at the moment, and even the skype test call was offline last night on the beta version but still available when I closed the beta and opened the old version.

I shall keep trying to figure out what is going on with the new version and will try to update my findings on this thread as much as I can.

---

### Post by tinker123 on 2017-04-05
I reinstalled the old Skype for Linux, version 4.3, from the repo.

It will not take my email address, which is my Skype userid.   It wants a "Skype Name".

On the skype site, I could not find anywhere to create a "Skype Name".   I went to Google and saw this is a problem for many people.  It looks like the UI was removed.

I created a second Skype account, choosing the option to use a phone number, instead of the email address for the userid.

Anyone know if Skype 4.3 will accept a phone number?

Thanks either way.

---

### Post by ajgreeny on 2017-04-05
> **tinker123 said:**
> I reinstalled the old Skype for Linux, version 4.3, from the repo.

It will not take my email address, which is my Skype userid.   It wants a "Skype Name".

On the skype site, I could not find anywhere to create a "Skype Name".   I went to Google and saw this is a problem for many people.  It looks like the UI was removed.

I created a second Skype account, choosing the option to use a phone number, instead of the email address for the userid.

Anyone know if Skype 4.3 will accept a phone number?

Thanks either way.
No idea about using a number rather than a username, but why not use a name like your current forum username, tinker123, which I am sure should be acceptable.
Or were you asking about using skype to contact, ie ring mobile or landline phones?  If that is what you were asking then the answer is Yes, you can make a phone call to a real telephone by entering the international phone number.

Incidentally, having read the skype forum yesterday, it appears that the "old" 4.3.0-37 version will remain viable and usable for some time, and there are no plans to stop it being used, contrary to what I and many others thought was going to be the situation.

---

### Post by tinker123 on 2017-04-05
[QUOTE=ajgreen]No idea about using a number rather than a username, but why not use a name like your current forum username, tinker123, which I am sure should be acceptable.
[/quote]

There is nowhere in the API for creating or editing a Skype account to insert a username.  I searched on Google, it was intentionally removed.

> 
Or were you asking about using skype to contact, ie ring mobile or landline phones?  If that is what you were asking then the answer is Yes, you can make a phone call to a real telephone by entering the international phone number


No, I am trying to make video calls.

---

### Post by tinker123 on 2017-04-05
I think I made progress with 4.3.

I saw an option to sign in with the "Microsoft Account" which allowed me to login  with my email address.  The camera icon was not grayed out this time.

I need to test the video call feature.  If anyone would like to help me out with a 30 second chat in that regard please PM me.  I have a business call coming up in about two weeks I need to have this ready for or convince the other party to use Google Hangouts instead.

Thanks.

---

