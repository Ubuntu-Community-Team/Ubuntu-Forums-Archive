---
title: "A couple of things need to be fixed"
date: 2010-03-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by arashiko28 on 2010-03-24
This is my testing experience so far, it's limited to my laptop with the specs you can see at my signature.

Comparing with all the previous releases I've used (since 7.04), this is by far the most stable one, no kernel panics, works out of the box with little to no twitches needed in some areas.
I use a 64-bit computer and OS.

The main thing is being asked 4 times in a row for my password in order to unlock keyring for wifi, even though I check the box > Automatically unlock this keyring whenever I'm logged in the problem persist every time I log out or restart. Also the wifi password don't have a remember check box anymore, and I have to type it every time i log in, it's annoying.

What's with this empathy stuff and that weird dialogue box? Do I always have to go to Applications> Internet > empathy to see my contact list? Not so attractive for new users.

The buttons on the left: there should be an option for the user to choose whether R/L position and if design team don't wan to change it, at least change the order from -maximize-minimize-close to -close-minimize-maximize

SOUND!!! This comes dragging from Karmic, why on earth take something that works perfectly fine and change it for something half understandable?? The sound preferences are as useless as a blank box in the middle of the screen. And the options I get are far from needed. If I plug earphones, still the speakers have sound, integrated mic doesn't work properly I can amplify but can't record!

Having to modify the alsa-base.conf file to add a line is nothing, but every time, what used to work on the previous version, now doesn't, and have to go through about 22 options, looking for the one that will work now. (This means restarting all of this times!!!!)

And last but not least, I keep getting a crash report, I already know it's not important the bug it's the fact that the message is shown, BUT, there are others like some butterfly and when I try to report it, shows an extended list of "obsoletes" packages that I should update/upgrade, but where? I have updated already and this message keeps appearing.

This is my mini rant, I like it overall, just as usual needs a couple of twitches.

---

### Post by arashiko28 on 2010-03-25
I've been looking for the way to report the keyring part, but I don't know how to do it.
How can I report something that the system thinks is OK?

I'm being asked to unlock keyring for wifi up to 4 times every time I log in and don't get to remember the password for the wifi. And most of times, networking is not enabled.

How do I report this to the development team?

---

### Post by ubername on 2010-03-25
> **arashiko28 said:**
> I've been looking for the way to report the keyring part, but I don't know how to do it.
How can I report something that the system thinks is OK?

I'm being asked to unlock keyring for wifi up to 4 times every time I log in and don't get to remember the password for the wifi. And most of times, networking is not enabled.

How do I report this to the development team?

You could try Accessories>Password and Encryption keys. Click Help and then 'Report a problem'.

---

### Post by lavinog on 2010-03-25
You can use a blank password for the keyring...this will prevent it from asking you.
to start the keyring manager use seahorse

---

### Post by uBeer on 2010-03-25
```
ubuntu-bug name-of-package
```

So for you that will be something like:
```
ubuntu-bug gnome-keyring
```

If you run ubuntu-bug without argument you get a dialog box with some questions. Good luck!

---

### Post by yzarc on 2010-03-25
here it is asking password to close the calendar. :D

---

### Post by RichardRicardo on 2010-03-25
I agree with you about the contact list. It can also be accessed by the envelope icon in the tray, but either way it is all over the place.

The me menu is great, but don't think that accessing my account preferences happens more often than accessing my contacts. This seems a little counter-intuitive, not something I would do on the fly with a lot of frequency.

Why can I not change my im status from the me menu if I am offline?

The me menu just seems a little weird. I can broadcast, change my status (if online), but the other option is to monkey with the account settings or ubuntu one preferences? I think I would prefer to see my contacts, open conversations or email.

I like the buttons on the left.

---

