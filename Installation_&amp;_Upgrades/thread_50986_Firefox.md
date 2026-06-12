---
title: "Firefox"
date: 2005-07-22
forum: Installation &amp; Upgrades
---

### Post by dccd on 2005-07-22
Hi, i have just installed kubuntu and i want to install firefox.
Doing this

sudo apt-get install mozilla-firefox

i have the following error

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mozilla-firefox: Depends: firefox but it is not installable
E: Broken packages

What did I wrong ??
Thanks for your help

DccD

---

### Post by bored2k on 2005-07-22
1. [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
2. sudo apt-get update
3. sudo apt-get install mozilla-firefox
4. sudo apt-get install flashplugin-nonfree

---

### Post by dccd on 2005-07-22
Hi thanks for your answer,

i have changed the sources.list file but i still get the same error ....

DccD

---

### Post by bored2k on 2005-07-22
[QUOTE=dccd]Hi thanks for your answer,

i have changed the sources.list file but i still get the same error ....

DccD[/QUOTE]
 O.o I'm sleepy so I wont try to solve _that_ problem now. Instead, you could try the Linux installer found on Firefox's website. [http://download.mozilla.org/?product=firefox-1.0.6&os=linux&lang=en-US](http://download.mozilla.org/?product=firefox-1.0.6&os=linux&lang=en-US)

Once you download it, right click - properties >permission and checkmark on all Execute boxes. After that is done, close and double click/click on the file > Run. That should run the very easy installer.

---

### Post by dclaridge on 2005-07-22
Is there any advantage to installing through apt-get rather than using general linux installers on application homepages?

---

### Post by bored2k on 2005-07-22
[QUOTE=dclaridge]Is there any advantage to installing through apt-get rather than using general linux installers on application homepages?[/QUOTE]
 The only ones I can think of right now (6am no sleep, bear with me) is that packages like java and flash would need for you to manually link them. Also, installing it like this only installs it for your user.

---

### Post by daninchina on 2005-07-26
I'm a little puzzled.

I (apparently) have just upgraded firefox to version 1.0.6 today.

However, although I've even updated my links (now I'm linking to /usr/bin/firefox instead of the installer file I had been using for version 1.0.4 which was in my home folder...) - whenever I check the software version in the "about firefox", it is still displaying as 1.0.6.

Even when trying to execute the program from a terminal, I get the same thing - it's always version 1.0.4.

According to Synaptic, however, my system is definitely up to date.

What do I need to do to actually use version 1.0.6?

Thanks!

---

### Post by daninchina on 2005-07-26
I have figured my problem out already; I just was a little impatient.

Although I had updated Firefox via synaptic, I did that while firefox was running.

Then, after altering the links to the updated version of firefox, I was still running Firefox's auto-updates for the themes I had been using (and it was really slow, for some reason).

After that finally finished up, I closed down all of my firefox sessions.

Then, when I tried to restart firefox, I found that I was running version 1.0.6.

Now that I understand where firefox should be kept and I am running version 1.0.6, is it safe to delete the 1.0.4 version that I had been using which was stored in my home folder?

Kindly advise.

Thanks,

 -Dan

---

