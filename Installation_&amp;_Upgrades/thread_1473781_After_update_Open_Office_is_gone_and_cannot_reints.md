---
title: "After update Open Office is gone and cannot reintsall"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by irenaios on 2010-05-05
I am using Ubuntu Hardy via the Dell Mini.

Quite awhile ago I upgraded my OO to the newest lpia version I could find...I cannot recall, but I did it "manually" by adding the launchpad repository etc.

Yesterday I noticed that my update manager was flashing at me and telling me I had updates and so I let it update. Afterwards I noticed that my Open Office would not work...in fact it was almost as if it was uninstalled. It was nowhere to be found.

So, I thought maybe my update got messed up and I ran it again with update manager - no changes. 

Okay...reinstall OO. I first tired "Add/Remove" and I got an error as soon as I clicked on the box next to the suite: "This application conflicts with other installed software...conflicting software must be removed...switch to Synaptic"

Okay...fine

When I mark OpenOffice.org for intsallation I get the pop up for "Mark additional required changes" which I say yes too and then another error:

"Could not mark all packages for installation or upgrade. The following packages have unresolvable dependencies. Make sure all required repositories are added and enabled in the preferences"

It then lists about 10 packages such as "openoffice.org-base....-calc....-filter-binfilter etc etc

I know I have the repositories chosenand I believe they are enabled:

[http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) hardy main
[http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) hardy main (Source Code)


Well can anyone help??? I really want my Open Office back!!!

Thanks!

James

---

### Post by wilee-nilee on 2010-05-05
Open office has in the past caused me a few problems, so I just have gone to synaptic right click mark for complete removal everything ticked OO then go to home hit crtl-h to show hidden remove the open office file, then just install again from command line. You can also look in synaptic if there are dependencies that can be found by right click on any broken or marked for install OO. The full purge should fix this though.

---

### Post by irenaios on 2010-05-05
Thanks for the response...

As far as I am able to tell nothing remains of OO in the package manager installed listed. I went ahead and went to HOME and did ctrl-h and sure enough there were two copies of OO folders (one was *2) - I deleted them both.  Thinking this solved my problem, I went back and tried to install using synaptic and I STILL get the exact same error.

Can you remind me how to do the install via command prompt? I cannot recall...I need to keep in mind that I need the LPIA version and NOT i386.

Appreciate the help!
J

---

### Post by wilee-nilee on 2010-05-05
> **irenaios said:**
> Thanks for the response...

As far as I am able to tell nothing remains of OO in the package manager installed listed. I went ahead and went to HOME and did ctrl-h and sure enough there were two copies of OO folders (one was *2) - I deleted them both.  Thinking this solved my problem, I went back and tried to install using synaptic and I STILL get the exact same error.

Can you remind me how to do the install via command prompt? I cannot recall...I need to keep in mind that I need the LPIA version and NOT i386.
Appreciate the help!
J
So what is the error again, and make sure everything even possibly associated with OO has been completely removed.
Did you look for all things OO with not the quick search but the full search in synaptic this includes the language association, I think you didn't remove everything then went to remove the files in home. I don't know the commands to purge or install OO sorry.

---

### Post by irenaios on 2010-05-05
When I check for install the "openoffice.org suite" I get this:

"Could not mark all packages for installation or upgrade. The following packages have unresolvable dependencies. Make sure all required repositories are added and enabled in the preferences"

And then 

"openoffice.org:

Depends: openoffice.org-base but it is not going to be installed
Depends: openoffice.org-calc but it is not going to be installed
Depends: openoffice.org-core but it is not going to be installed

etc"

I then tried to check each of these individually and I just continue to get more of the same type of errors with different dependency errors. 


The ONLY thing I can find that mentions openoffice that is still installed are some language files such as 

language-pack-gnome-en-base
language-pack-en-base
language-pack-kde-en-base
libhunspell-1.1-0
myspell-en-us


That's it. You think it's okay to uninstall those too? I wasn't sure if they were needed for other programs too.

Thanks again!
J

---

### Post by wilee-nilee on 2010-05-05
> **irenaios said:**
> When I check for install the "openoffice.org suite" I get this:

"Could not mark all packages for installation or upgrade. The following packages have unresolvable dependencies. Make sure all required repositories are added and enabled in the preferences"

And then 

"openoffice.org:

Depends: openoffice.org-base but it is not going to be installed
Depends: openoffice.org-calc but it is not going to be installed
Depends: openoffice.org-core but it is not going to be installed

etc"

I then tried to check each of these individually and I just continue to get more of the same type of errors with different dependency errors. 


The ONLY thing I can find that mentions openoffice that is still installed are some language files such as 

language-pack-gnome-en-base
language-pack-en-base
language-pack-kde-en-base
libhunspell-1.1-0
myspell-en-us


That's it. You think it's okay to uninstall those too? I wasn't sure if they were needed for other programs too.

Thanks again!
J

I am not sure about the specific language pack for OO, what I do know is that every thing OO has to be removed before you will get the install. You only have to look with open office in the deep search in synaptic. You might set the preferences in synaptic to show the information bar in the bottom widow that will show you the dependencies. You might also consider installing ubuntu tweak the ppa and in that is the open office ppa link. The tweak will also help get rid of cache and configuration files. also in the terminal sudo apt-get autoremove & sudo apt-get autoclean are good ways to clean.

Right now I am doing a upgrade on a thumb from Karmic to Lucid to see the grub gui that is causing some problems with upgrades. So I can't open synaptic to look around.

---

### Post by irenaios on 2010-05-06
Following the Instructions offered to Tony Land here:
[http://www.rebelzero.com/ubuntu/ppa-for-openofficeorg-301-for-hardyintrepid/94](http://www.rebelzero.com/ubuntu/ppa-for-openofficeorg-301-for-hardyintrepid/94)

I was able to revert back to 2.4 (I think I was using 3.0)

Whew.

Still don't know what happened, but it sounds like the same thing that happened to Tony.

---

