---
title: "Inconsistent dialogs and modifiers on core ubuntu applications"
date: 2009-02-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by QwUo173Hy on 2009-02-12
This issue actually effects Ubuntu historically and not just in Jaunty, but it's a pretty serious issue I think.

When exiting an application, a dialog may appear giving you choices on how you would like to exit (Save / Discard / Cancel). These are  handled inconsistently by the various core applications. Most troubling is that key modifiers (eg. ALT+C to choose "Cancel) are available, and therefore encouraged for these dialogs.

This has led to a few accidents for me and I'm sure other users, and it forces the user to put a lot of thought into what should be a routine operating.

Just to compare, look at this:

```
Application	Cancel Mod	Save Mod	Discard Mod

Gimp		C		S		N
Gedit		C		A		W
OOo		no modifier	S		D
Evolution	C		S		D

```
You can see from above that each application has it's own way of handling this situation and no two are alike. This means that the user, even if familiar with the applications, has to read each message word for word. Personally, I wouldn't dare get used to a keyboard modifier shortcut in case I used the wrong one on the wrong application.

Would it be possible to centrallize the location of these strings and their modifiers, in gconf for example? The applications could then retrieve them, ensuring consistency.

I'm going to report this as a bug, but I thought that someone might be able to make a useful addition (or subtraction!) to my report before I submit the bug report.

---

### Post by garba on 2009-02-12
this is a very good point, this would make a fine addition to the gnome HIG, gnome/gtk apps should stick to a default, common dialog for these kinds of tasks

---

### Post by xerosis on 2009-02-12
OpenOffice is a bit of an exception being that it's a java app rather than a gtk one.

---

### Post by QwUo173Hy on 2009-02-13
> **xerosis said:**
> OpenOffice is a bit of an exception being that it's a java app rather than a gtk one.

I don't think so. Ubuntu maintainers package OpenOffice themselves and provide it as a core application, i.e. in the Main repository.

They modify OpenOffice already for example by making the GUI more consistent with the Human theme (AFAIK) so making these adjustments would simply be taking their "visual consistency" ideals and applying it to the functionality / workflow of the desktop in general.

---

### Post by inportb on 2009-02-13
OpenOffice.org is *not* a Java application. Only a small (and nonessential, imo) part relies on Java, and that can be disabled to conserve resources.

But back to the topic -- I think this is a great idea for usability.

---

### Post by Nullack on 2009-02-13
I say bug it on LP and the gnome bugzilla :) Its a good find.

---

### Post by QwUo173Hy on 2009-02-13
I've put it on Launchpad [https://bugs.launchpad.net/ubuntu/+bug/329185](https://bugs.launchpad.net/ubuntu/+bug/329185)

But the formatting of the table I did for the modifiers came out terrible :( But I linked back here anyway.

I have no problem reporting on gnome-bugzilla, but I assume I need to remove OpenOffice from the equation since they don't distribute it with gnome.

---

### Post by bruce89 on 2009-02-13
This goes beyond what the GNOME HIG can do. It only specifies guidelines. Perhaps a [GNOME goal]("http://live.gnome.org/GnomeGoals") would be better.

---

### Post by QwUo173Hy on 2009-03-01
I received an email response to one of my postings somewhere. I've been directed by a gnome-love member to contact Gnome Desktop Devel mailing list. I'll keep you posted.

---

### Post by nyarnon on 2009-03-01
> **jarlath said:**
>  This means that the user, even if familiar with the applications, has to read each message word for word. Personally, I wouldn't dare get used to a keyboard modifier shortcut in case I used the wrong one on the wrong application.

Are you saying you can only remember one set that you would then use for all apps?

Personaly I remember them per app and even per OS. Remember that the settings for f.i.  firefox windows and linux are in different places.

Although I do think some unification is beneficial, I would like to point out that this is not really a realistic goal. Hence IMHO this is just a waste of every-bodies time and resources. And most certainly not something to enter in the bugreporting system.

---

### Post by bcat on 2009-03-01
> **nyarnon said:**
> Although I do think some unification is beneficial, I would like to point out that this is not really a realistic goal. Hence IMHO this is just a waste of every-bodies time and resources. And most certainly not something to enter in the bugreporting system.

I disagree. First of all, isn't it a bit early to say it's not a realistic goal? Maybe all it will take is someone willing to draft a specification of sorts for this and write some patches for common applications. As for whether or not it belongs in Launchpad, I honestly don't know, but I can't think of any reasons it doesn't. Not all bugs are about programming errors. There are also enhancement requests, polish bugs, etc.

---

### Post by nyarnon on 2009-03-02
> **bcat said:**
> I disagree. First of all, isn't it a bit early to say it's not a realistic goal? Maybe all it will take is someone willing to draft a specification of sorts for this and write some patches for common applications. As for whether or not it belongs in Launchpad, I honestly don't know, but I can't think of any reasons it doesn't. Not all bugs are about programming errors. There are also enhancement requests, polish bugs, etc.

You think it's realistic? How come? Still trust the ISO institute? The reason it doesn't belong in the bug system is because it's not a bug. Yes put in a enhancement request, preferably with the author of the app. See how realistic that goal is.

---

### Post by amano on 2009-03-02
C'mon. What we don't need here is a philosophical discussion on what is a bug and what not. 

Unconsistent dialogs within Ubuntu (at least main) are certainly things that should be fixed and therefore belong into the bugtracker.

A good catch by the thread-starter BTW, congrats ;)

---

### Post by nyarnon on 2009-03-02
I strongly disagree. If under Ubuntu (only Ubuntu) f.i. the keyset for ooo would be changed for cosmetic reason, I'm off this platform.

---

### Post by mpt on 2009-03-02
> **nyarnon said:**
> You think it's realistic? How come?

Because Windows manages this kind of consistency 95% of the time, and Mac OS manages this kind of consistency 99% of the time. (They mess up with other kinds of consistency, but that’s a separate topic.) Ubuntu should be able to achieve it too. It’s not for “cosmetic reasons”; it’s so that you can dismiss dialogs, even dialogs you use only occasionally, without even looking to see what the access keys are. That makes the OS faster to use.

Thanks for picking this up, jarlath.

---

### Post by nyarnon on 2009-03-03
You cannot compare Ubuntu to windows or apple. Both the latter systems are centrally governed, whereas Ubuntu is just one of many distro's carried by a huge multifaceted community. Therefore it is important that proposed changes would be carried by the developers of the app and not by a single distro. 

Therefore any changes made by only Ubuntu would indeed be cosmetic they would give Ubuntu a different look as opposed to other distro's. 

Now imagine all distro's would start doing this and amend interface changes to unify their desktops. No don't even try, the HORROR.

---

### Post by QwUo173Hy on 2009-03-03
Someone on the devel' list gave me a link to a specification for dialogs [here]("http://library.gnome.org/devel/hig-book/stable/windows-alert.html.en"). See section 3.4.6.1.&#8195;Save Confirmation Alerts.

I'll read it later when I get home. Besides someone pointing me to this there hasn't been much reaction yet but if it seems that some apps are off-spec, I'll contact the application developers.

If it seems that the spec itself allows this much varience then whoever maintains or writes the specs needs to be contacted.

Thanks for the encouragement by the way. In spite of what another poster said, I think this situation is very clumsy. I'm a business user and although I love both Ubuntu and my job, I really don't like wasting time reading dialogs that I can zap in the blink of an eye on other systems.

---

### Post by QwUo173Hy on 2009-03-03
Okay, now that I've read it, it seems that there is a specific spec for behaviour, and it applies to all (gnome) applications regardless of the document type.

I'll contact the maintainers of the apps I've listed in the first post, as well as the Ubuntu maintainer for OpenOffice. There are a few other apps like file-roller that should probably be checked too, as someone suggested.

---

### Post by nyarnon on 2009-03-03
Now we are talking. That' s the only way to go. Good for you. Good that someone is going on that quest, although a do think there is a little DonQuichottery involved here :lolflag:

---

### Post by Kow on 2009-03-03
If it is something that hinders the goals of ubuntu then it is definitely an ubuntu bug. Ubuntu strives for a professional look and inconsistent dialogues in GNOME apps are not professional. Therefore, it is a bug. I would think GNOME would want consistency among their apps so this likely applies to them too. Since it likely applies to them, let them deal with it and save us some work. Little things like this should be easily fixable by 2.26 release.

---

### Post by amano on 2009-03-03
> **nyarnon said:**
> If under Ubuntu (only Ubuntu) f.i. the keyset for ooo would be changed for cosmetic reason, I'm off this platform.

That's the beauty of choice. But your possible leaving is no reason for a bug not to be fixed.

---

### Post by QwUo173Hy on 2009-03-04
Okay, I've gone through all of the core Gnome apps bundled with Ubuntu, as well as others that are not Gnome but still bundled. See the chart and comments in the attachment.

If anyone has anything to add, or if I've missed something, please tell me before I go contacting maintainers.

[http://dl.getdropbox.com/u/464104/close-dialogs-in-gnome.ods](http://dl.getdropbox.com/u/464104/close-dialogs-in-gnome.ods)

---

### Post by nyarnon on 2009-03-04
> **amano said:**
> That's the beauty of choice. But your possible leaving is no reason for a bug not to be fixed.

Thats all in the eye of the beholder what you call bug fixing, I call bug introducing. I work with several distro's and I'm not planning to learn complete new behaviour just for Ubuntu. If anything like this is to be undertaken you have to do it at developer level.

---

### Post by nyarnon on 2009-03-04
> **jarlath said:**
> Okay, I've gone through all of the core Gnome apps bundled with Ubuntu, as well as others that are not Gnome but still bundled. See the chart and comments in the attachment.



I count a total of 8 apps? Wrong sheet?

---

### Post by QwUo173Hy on 2009-03-16
It looks like the gimp developer has patched for this. I only posted to the mailing list a few days ago so that's great. Thanks Sven!

2009-03-16 Sven Neumann <sven@gimp.org>
 	
 	* app/display/gimpdisplayshell-close.c
 	(gimp_display_shell_close_dialog): adapt button labels to the
 	latest GNOME HIG.

---

### Post by nyarnon on 2009-03-16
Good work, now start praying that the Gnome HIG == KDE HIG,

---

### Post by Joe_Bishop on 2009-03-16
Like GIMP variant the most. Wonder if it would be default.

---

