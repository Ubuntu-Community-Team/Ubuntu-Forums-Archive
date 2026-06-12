---
title: "Bare-Metal Rebuilds"
date: 2011-04-13
forum: Installation &amp; Upgrades
---

### Post by coljohnhannibalsmith on 2011-04-13
Hi,

Being the adventuruous type that I am, and regularly committing myself to difficult installs of very complex software, I occasionally 'hose' my OS.  This is in addition to the normal difficulties that harry the ordinary user; such as losing 'gnome-panel,' on start-up; and I'm consequently forced to occassionally rebuild my OS from ***bare-metal.***

During this *learning-process*, I've discovered a way to minimize the difficulty of this.

Here's what I've discovered:

During the process of making regular backups, I've also started saving the ***Full State*** of "Synaptic Package Manager" to a text file, so that in the event that I do something that permanently damages the OS, I have a *partially-automated* form of recovery.  What I do is read this file back into Synaptic, after I've established a network connection, and let Synaptic do the work of reinstallation, rather than do it myself, by hand and by memory.

I've also started saving my software-sources to a text file.  But, I'm currently doing this by hand; because, I don't believe software-sources will allow the saving of an external text file.

This usually works pretty well; but I've also significantly customized my menus, and there's no way of saving these settings externally, either.  So, after a complete rebuild, I'm left reconfiguring the menus by hand, and let me tell you; this is really tedious... 

What I'd like to suggest is that this feature be added to both the menuing-system, and to software-sources.  These changes will be a real time-saver, in the event of an irreversible OS event.  The entire process could then be completely automated, *by a shell-script, perhaps?????* 

Also, It would not surprize me, to learn, that some of you have already figured-out how to save these settings to a file.  If so, can you please share this with me?  IMHO, Ubuntu *disaster-recovery* could stand some improvement.


For those of you who haven't thought about this, I've attached both of these files from one of my systems, to further illustrate this...



Thanks, Hannibal


Oh wait...  This just occurred to me.  I've forgotten all-about the ***"configuration-files"***... Here are my thoughts on this...  There also needs to be some-kind of 'snap-shot' taken of these that's saved to a single file, that can be restored in the manner previously mentioned.  The difficulty arises, that these files are stored in random locations, all thoughout the file system.  I can think of two ways to handle this.  The first, and I think the simplest, is to designate one-specific folder for configuration files ***system-wide.***  Alternatively, they could be stored to a database file, in the afore-mentioned *'configuration-folder' or*, it could be a single text file; but then no-human would have the patience to read it. Even better, a 'hybrid-solution;'

1. Designate one-specific folder, as the system-wide ***"configuration-folder."***

2. Keep each application's configuration settings in a separate text-file, the way they are now, for ease of editing, and start-up performance.

3. Also, keep track of these settings in a central-database.

4. Also, store a back-up of these settings, in a ***master-text-file,*** that can be read by the central-database, in the event of a database failure.

5. The 'Master-Text-File' would be the only file a user would have to save externally to restore all of his configuration settings...


[Forget about the second-way; it was a red-herring.  I'll stick with the five steps above.]


Hmmm.  [B][I]Did I just design a versioning-system?????


P.S., With all of the configuration files stored in the same folder, it would be possible to just make an archive of the entire folder, and then restore the entire folder from the archive in the event of a failure.
[/I][/B]

---

