---
title: "Cant Run Gnome Xchat"
date: 2008-09-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Nullack on 2008-09-18
Im stuck on this. It wont run, Ive tried reinstalling it as well as purging and then installing.

It executes, but doesnt display anything, then just sits as a process until I kill it.

In terminal I get:

nullack@PPP:~$ xchat-gnome
*** glibc detected *** xchat-gnome: double free or corruption (out): 0x0000000001b43f60 ***

Anyone?

---

### Post by ronacc on 2008-09-18
I just installed xchat-gnome to check for you and it started right up and signed on to channel #ubuntu , I'm amd64 here if that makes a difference , any tests I can run for you ?

---

### Post by nanomad on 2008-09-18
Xchat-gnome works fine here
Ubuntu Interpid x86
xchat-gnome version: 1:0.23.92-0ubuntu1
xchat version: 2.8.6-2ubuntu1

---

### Post by Nullack on 2008-09-18
Thanks guys - Ive bugged it. Couldnt happen at a worse time while I need to be discussing the iso tests on IRC. I need to find a workaround. The other IRC clients in the repos drove me mad.

[https://bugs.launchpad.net/ubuntu/+source/xchat-gnome/+bug/271734](https://bugs.launchpad.net/ubuntu/+source/xchat-gnome/+bug/271734)

I cant figure this bug out.

---

### Post by ronacc on 2008-09-18
try the regular xchat (not gnome) , do you mabye have a non standard version of glib ?

---

### Post by plun on 2008-09-18
Chatzilla is another option

[https://addons.mozilla.org/en-US/firefox/addon/16](https://addons.mozilla.org/en-US/firefox/addon/16)

With pure Firefox...:)

---

### Post by Nullack on 2008-09-18
The normal xchat segfaults everytime I try to run it beyond the connect to server screen. Ill need to do another bug report about that.

Synaptic says there is a glibc-doc and a glibc-source. Can anyone please advise what the name of the real glibc used in runtime is please.is it linux-libc-dev?

---

### Post by ronacc on 2008-09-18
I think this is it, libglib2.0-0  (the Glib library of C routines ) , my installed version is 2.18.0-1  , IIRC it was updated a few days ago but I had to dist-upgrade to get it . check synaptic for upgradeable but held back packages .

---

### Post by Nullack on 2008-09-18
Ive reinstalled all those libglib entries. Can anyone please confirm a default install will have:

libglib2.0-0
libglib2.0-cil
libglibmm-2.4-1c2a
libglib-perl

I still get the "double free or corruption" error.

---

### Post by ronacc on 2008-09-18
confirmed , and I have added my installed versions.
libglib2.0-0      2.18.0-1
libglib2.0-cil    2.12.1-1ubuntu2
libglibmm-2.4-1c2a    2.17.3-1
libglib-perl     1:1.183-1

and 
xchat-gnome     1:0.23.92-0ubuntu1

---

### Post by Nullack on 2008-09-19
Well there was a things I wasnt sure about with the iso test install I did so I did a full format and clean install of A6, but the problem remains. Interestingly it works under valgrind.

---

### Post by ronacc on 2008-09-19
hmm the question mabye becomes why does it run for me ? I've got the A6 live cd d/l'ing now I'll try that and see what happens ,it will take a couple of hours to get it down my connection is slow .

---

### Post by Nullack on 2008-09-19
Sebastien has once again shown why he's a master programmer by going through the valgrinds I did which led to this:

[https://bugs.launchpad.net/ubuntu/+source/enchant/+bug/261596](https://bugs.launchpad.net/ubuntu/+source/enchant/+bug/261596)

---

### Post by ronacc on 2008-09-19
what language are you using for spellcheck ? I am english (united states) here so why am I not getting the crash ?

---

### Post by ronacc on 2008-09-19
ok I just booted the  A6 livecd , 64bit  ,installed xchat-gnome and it runs ok from the live cd . If you are running a language for spell check other than english (united states) I'll switch to that and see what happens .

---

### Post by Nullack on 2008-09-19
Thanks mate, my location is Australia, Sydney and Im using whatever default language ubiquity selects. My home office is powered down for ups maintenance and Im on my partners macbook so I cant look it up right now sorry.

---

### Post by ronacc on 2008-09-19
thats alright I'm going to be out for the next few hours and couldn't respond anyway , I'll check when I get back . I'm eastcoast US here so we are 180 degrees out of sync.

---

### Post by Nullack on 2008-09-20
From synaptic:

aspell-en
hunspell-en-us
laguage-support-en
lanuage-support-writing-en
myspell-en-au
myspell-en-gb
myspell-en-za
openoffice.org-l10n-en-gb
openoffice.org-l10n-en-za
wamerican
wbritish

---

### Post by Starks on 2008-09-20
I really hate Gnome Xchat. Unlike the regular Xchat, you can't be on more than one server at a time, AFAIK.

---

### Post by Nullack on 2008-09-20
xchat is even worse - it segfaults on launch everytime.

---

### Post by alienexplorers on 2008-09-20
All I use is xchat since gnome xchat fails on my system.

---

### Post by ronacc on 2008-09-20
In synaptics I show the files you listed plus 
language-pack-en
language-pack-en-base
language-pack-gnome-en
language-pack-gnome-en-base
language-selector
language-selector-common

I do not show the openoffice files you show what Ihave is
openoffice.org-l10n-common

I do not show  wbritish

also what language is checked in your xchat-gnome preferences for spellchecking?

---

