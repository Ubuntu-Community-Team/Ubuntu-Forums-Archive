---
title: "Why are so many packages removed for the upgrade??"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by johann_p on 2008-04-30
I just started the upgrade from Gutsy to Hardy and I get informed that "110 packages are going to be removed".
Among those are packages like cinepaint, icepodder, esound, mono, myspell-de-at, xcalc ...

I want these packages, why does Ubuntu remove them?

What is going on here?

I canceled the upgrade because I do not want all these packages to get removed. :(

---

### Post by Sef on 2008-04-30
Those packages will be updated or removed if there are other packages replacing them.  Any upgrade provides newer packages than the existing ones as well as new packages that were not in the operating system.

---

### Post by elustran on 2008-04-30
I chose to not remove those packages.  I didn't want to remove something that might have been used by another program.  If that will cause a problem, is there any way to remove them after I've upgraded?

---

### Post by johann_p on 2008-04-30
> **Sef said:**
> Those packages will be updated or removed if there are other packages replacing them.  Any upgrade provides newer packages than the existing ones as well as new packages that were not in the operating system.

I do not understand: if the package is newer, will it not just get updated as thousands of other ones?
And if there is a replacement package, I should at least find it in the list of newly installed packages .. but I cannot find most of the ones that interest me. There is nothing similar to icepodder in the list of newly installed packahes.

I find this highly irritating: if there is some reason why a package must be removed, why isn't Ubuntu telling me about that reason?
If there is an alternative for a package that Ubuntu wants to install, why isn't Ubuntu informing me about that alternative so I can make a decision?

Is there a way to tell Ubuntu that it should NOT remove those packages or do they HAVE to get removed?

I have 3053 packages installed now in Gutsy and I had a reason to install all of them. Now I want a reason why Ubuntu wants to remove them.

---

### Post by johann_p on 2008-04-30
> **elustran said:**
> I chose to not remove those packages.  I didn't want to remove something that might have been used by another program.  If that will cause a problem, is there any way to remove them after I've upgraded?
How? I only get the choice between starting the upgrade and accepting everything Ubuntu decided to do or cancelling the upgrade :(

---

### Post by mivo on 2008-04-30
They were probably renamed or replaced, or meta packages changed.

---

### Post by elustran on 2008-04-30
yes, but will there be a problem if they're kept, and if so, is there a way to uninstall them?

---

### Post by johann_p on 2008-04-30
> **mivo said:**
> They were probably renamed or replaced, or meta packages changed.
So does this mean I do not have to worry about losing any of the software after the upgrade?

---

### Post by mivo on 2008-04-30
I'm fairly sure that you don't have to worry about losing any applications. If you do, though, they can probably be re-installed very quickly (settings are saved in your home partition, which the upgrade doesn't touch).

I should add a disclaimer, though: I always do a fresh install when I upgrade to the next Ubuntu version (separate home partition, so it's painless), because it's faster and, I feel, cleaner. So take my opinion with a grain of salt, though I think accepting the upgrader's choices is relatively risk-free.

---

### Post by elustran on 2008-04-30
I was hoping I wouldn't have to do a fresh install with this upgrade because I had heard that the newer version had improved installation capabilities.  So far, that hasn't been the case.  Maybe I shouldn't have upgraded - the only operable difference I notice is that things that worked before don't work now.  I'm getting a little tired of rewriting my config files all the time.

---

### Post by johann_p on 2008-04-30
> **mivo said:**
> 
I should add a disclaimer, though: I always do a fresh install when I upgrade to the next Ubuntu version (separate home partition, so it's painless), because it's faster and, I feel, cleaner. So take my opinion with a grain of salt, though I think accepting the upgrader's choices is relatively risk-free.
Hmm I have seen this recommendation fairly often and it puzzles me no end. I do have a separate home partition, but adapting a fresh install to the configuration i have now would be an extremely hard task that would need an extreme amount of effort to prepare:
There are dozens if not hundreds of configuration files for Apache, Mysql, etc, there are many packages I have installed in addition to what a default fresh install provides, many of them with their own system-configuration files. There is even data that is stored outside of the home partition by default (e.g. mysql databases, files for certain web applications etc.)

For anyone who is not just using a very basic system I think doing a fresh install is asbolutely not an option.

The bottom line is this: I had rather severe trouble during the last two upgrades (which I performed on about 3 computers each) and I am a bit scared of things getting messed up this time, because I need my computer for my work and for private matters.

I have waited a few days to let the mirrors cool down and to also let major problems surface.

I would love to upgrade this thing (if only because eventually all support questions will assume that I have Hardy) but I must admit that I am worried and that long list of packages to get deleted reinforced my worries somewhat.

---

### Post by arpanaut on 2008-04-30
If you have no really compelling reasons to upgrade at this point I would suggest that you wait until the "enterprise" release of 8.04.1 due out in June when many of these issues will be cleared up. Or work-arounds known.

There could be many reasons for the removal of those packages, Most likely they are not compatable with hardy as yet, dependency issues with hardy packages, depeciation of packages that these programs use and such... Many 3rd party packages do not upgrade gracefully.

My philosophy is... if it's fixed don't break it...

If you depend on your machine for work and everyday tasks, I would wait until these things are fixed, or you have researched the reasons why and what you have to do to solve these issues.

good luck!

---

### Post by johann_p on 2008-04-30
> **arpanaut said:**
> If you have no really compelling reasons to upgrade at this point I would suggest that you wait until the "enterprise" release of 8.04.1 due out in June when many of these issues will be cleared up. Or work-arounds known.

There could be many reasons for the removal of those packages, Most likely they are not compatable with hardy as yet, dependency issues with hardy packages, depeciation of packages that these programs use and such... Many 3rd party packages do not upgrade gracefully.

My philosophy is... if it's fixed don't break it...

If you depend on your machine for work and everyday tasks, I would wait until these things are fixed, or you have researched the reasons why and what you have to do to solve these issues.

good luck!

Thanks for that advice, I think I will wait till June then and observe this ...

---

