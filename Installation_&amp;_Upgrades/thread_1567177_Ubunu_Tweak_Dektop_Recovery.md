---
title: "Ubunu Tweak Dektop Recovery"
date: 2010-09-03
forum: Installation &amp; Upgrades
---

### Post by xpawnrip on 2010-09-03
I saw a video about Ubuntu tweak yesterday and understood that you can backup all application using desktop recovery and than after reinstalling Ubuntu you can restore all the application with a single click. Is this right?Can Ubuntu Tweak Desktop Recovery do that?Because I backed-up my applications, I uninstalled 2 or 3 programs, and than i restored the programs using Desktop Recovery but nothing happened.Am I doing something wrong?
here's the video: [http://www.youtube.com/watch?v=J1tWk8o-Jw0](http://www.youtube.com/watch?v=J1tWk8o-Jw0)
Please help:([URL="http://www.youtube.com/watch?v=J1tWk8o-Jw0"]
[/URL]

---

### Post by quixote on 2010-09-05
As I understand it, Ubuntu Tweak just saves all the Desktop **settings**, saves which applications are installed (not the apps themselves), and saves system settings.  That's different from, say, a Windows System Restore which is over a hundred megabytes even on old machines, and can actually restore your complete system to whatever it was when saved if your current one gets borked.  The Ubuntu Tweak saves take just a second, so no way that's actually saving the applications themselves. (And the guy in the video needs to talk slower too! :D)

So, when you uninstalled the programs and then used Desktop Recovery, it tried to make sure that if you had the program, your settings would all be the same as before.  Since the program didn't exist any more, it just did nothing.

Ubuntu badly needs a real recovery program, like the Windows one.  Right now the only way to come close is to use something like Clonezilla, or the command line "dd" to mirror your system partition, as well as backup your whole /home directory.  None of that is super hard, but it's not one-click easy either.

---

