---
title: "Language Support Dependency Madness"
date: 2008-05-30
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Mr. Picklesworth on 2008-05-30
Currently running Hardy with proposed update repository, I had some updates roll in that essentially wanted to wipe out half the software that I have installed. No, these were not all dependencies of ubuntu-desktop. These were odd things, like Planner, OpenOffice Writer and Base (but not Drawing or Presentation).
Some poking led me to believe that this turmoil was caused by the language support metapackages.

(I should also point out that I am not a fan of OpenOffice and prefer not to have it installed anyay).

Language support packages explicitly *depend*, via a surprising chain of events, on packages such as openoffice-core. This bothers me a lot. Firstly, it does not appear reasonable that language support should require such packages. If anything, those packages should require one of them (can we use regex for dependencies?), and at best the two should be entirely decoupled. I think valuable packaging lessons were learned with the messes associated involving ubuntu-desktop's broken dependencies. Similar madness occurs here, except potentially worse since this can be duplicated for every package which does language support in an unusual way. If there is going to be a language support metapackage, it *has to* install and uninstall in a way that does not carry unrelated stuff with it and in a way that does not assume what the user runs to be vanilla Ubuntu. Otherwise, this platform can never be called sane or scalable. Perhaps it is something that could be addressed in Intrepid.

Another problem seems to go deeper into Debian's infrastructure, which is that this metapackage depends on an arbitrary and static set of other packages. What if the user installs some other unusual program with a whole lot of language support packages, but we don't want that language support package to waste space for everyone?

Debian offers a few tricks for dependencies, though I must admit to not knowing the real functional differences between depends, recommends and suggests. Is this fixable? Should we be filing bug reports on this sort of thing?

---

### Post by ronacc on 2008-05-30
this is a recuring madness that strikes every upgrade cycle ,dependencies that aren't . before something hits the repos there should be an independant check to see that the dependencies really are dependencies and not recomends or suggests .

---

### Post by Gina on 2008-05-30
I checked the update yesterday and it wanted to uninstall Firefox 3 and all the bits!  On trying Update Manager I found there was only a partial update available - so I left it.  Later the full update was available and I went ahead with Update Manager (I usually use apt-get from terminal).  This is a fairly frequent occurrance with the updates as some dependant modules hadn't reached the repos.  The update replaced the beta Firefox 3 with the final release :)

---

### Post by plun on 2008-05-30
Well... what is Ubuntu-desktop  ?

I notice this again and again that a lot is just junk for me (IMHO)

I just removes it.....  fonts never used and never used apps.

-------

The repos are probably over-filled with software that no ones uses.

-------

So what is Ubuntu-desktop.....  :confused:

---

### Post by nhandler on 2008-05-30
> **plun said:**
> Well... what is Ubuntu-desktop  ?

I notice this again and again that a lot is just junk for me (IMHO)

I just removes it.....  fonts never used and never used apps.

-------

The repos are probably over-filled with software that no ones uses.

-------

So what is Ubuntu-desktop.....  :confused:

ubuntu-desktop is a metapackage. A metapackage simply depends on a lot of other packages. This means that if you install ubuntu-desktop, all of its dependencies are also automatically installed. ubuntu-desktop depends on all of the packages in the Ubuntu desktop system. You can view its dependencies [here]("http://packages.ubuntu.com/intrepid/ubuntu-desktop").

---

### Post by hortimech on 2008-05-31
well I noticed that another update was required, so opened a terminal and ran sudo apt-get update && sudo apt-get upgrade, to be informed that several Openoffice updates would be held back. After a quick google, I found that apt-get dist-update was required, this removed the following:

language-support-en language-support-translations-en
openoffice.org-help-en-gb openoffice.org-l10n-en-gb
openoffice.org-l10n-en-gb-za

Never mind I thought (foolishly) I will just put back their replacements, but no, to replace them, I will have to remove Openoffice.

This is madness, surely it should work this way: base OS --> language support --> any program you want to install.

By the way, why do you get locales for just about every English speaking nation installed if you install GB locale?

And whilst I am having a rant, who came up with the way of selecting your locale whilst installing, that scrolling map is virtually impossible to use!

---

### Post by Gina on 2008-05-31
> **hortimech said:**
> This is madness, surely it should work this way: base OS --> language support --> any program you want to install.

By the way, why do you get locales for just about every English speaking nation installed if you install GB locale?

And whilst I am having a rant, who came up with the way of selecting your locale whilst installing, that scrolling map is virtually impossible to use!I agree on all that!

---

### Post by ronacc on 2008-05-31
> **hortimech said:**
> 

And whilst I am having a rant, who came up with the way of selecting your locale whilst installing, that scrolling map is virtually impossible to use!

stating facts is not a rant,  the only good thing about the locale selection is that you only have to deal with it once (per install).:lolflag:

---

### Post by hortimech on 2008-05-31
I asked the question on the OpenOffice forum and this is definitely seen as an Ubuntu problem

[Quote] 
Almost certainly not. OOo tries to adjust it's own locale to the system's one unless another locale is set explicitly. However, the Ubuntu build of OpenOffice.org has a bad reputation. They seem to add more bugs than features to the office.

Anybody care to tell me how I get my OS locales back, because I tried removing OpenOffice and got dependancy HELL! Locales seems to depend on parts of OpenOffice and NOT the other way round!:confused:

---

### Post by danbuter on 2008-05-31
Hmm,I deleted Open Office. Should I expect a bunch of problems with my regular install? That's the feeling I'm getting here, and it will seriously piss me off.

---

### Post by hortimech on 2008-06-01
Honestly, I do not know, I got Openoffice when I installed, then forced an update to it, DO NOT DO THIS!

it took off my locales and now I cannot get them back.
So, to the person (or persons) who thought it it was a good idea to make OpenOffice a dependency of locales, thanks, NOT

---

### Post by hortimech on 2008-06-02
Right, another update rolled up:
openoffice.org-l10n-common, this allowed me to put back the missing files
language-support-en language-support-translations-en
openoffice.org-help-en-gb openoffice.org-l10n-en-gb
openoffice.org-l10n-en-gb-za

except the last one is now openoffice.org-l10n-en-za, which I will not need because I live in ENGLAND not SOUTH AFRICA

So I tried to remove it, but it wanted to remove:
language-support-en language-support-translations-en

I WILL SAY IT AGAIN LOUDLY, I LIVE IN ENGLAND NOT SOUTH AFRICA, why does the ENGLISH language support in Ubuntu depend on the south africa language support of OpenOffice?????? and don't give me any stupid reasons like Ubuntu comes from south africa.

Also, would it not be a better idea to release all common related updates at the same time, this would stop idiots like me having problems.:)

---

### Post by fig_wright on 2008-08-19
I have this problem too. I am short of space, so I went hunting for things I didnt need. Spotted that OO has installed a splattering of locale language files for GB US AU ZA . When I try to delete the unneeded ones it tries to install:
language-support-en
language-support-translations-en
mozilla-firefox-locale-en-gb
thunderbird-locale-en-gb
It's utterly nuts that trying to uninstall a South African thesaurus would force the removal of Firefox's GB files!!:mad:

---

