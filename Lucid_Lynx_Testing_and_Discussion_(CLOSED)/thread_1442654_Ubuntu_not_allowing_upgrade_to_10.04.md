---
title: "Ubuntu not allowing upgrade to 10.04"
date: 2010-03-30
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kellanium on 2010-03-30
It gives me this error, no matter how I try to install the upgrade. I've tried network upgrading and the alternate CD and i can't figure out what's wrong. It worked fine when i upgraded my netbook. 

(The Error is in the attachment)

---

### Post by Mark Phelps on 2010-03-30
Lucid is still in beta testing, so you should be posting your 10.04 questions to the proper forum: Development & Programming, Lucid Lynx Testing.

I'm asking the Mods to move this thread there.  Look there for any responses.

---

### Post by sdowney717 on 2010-03-30
you have a package installed that is interfering with the upgrade. This happened to me with open office. I removed OO and the upgrade went ahead and worked.
But my message mentioned Open office. your message mentions pkgProblemResolver?

Found this here
[http://www.granularlinux.com/forum/index.php?topic=1487.0](http://www.granularlinux.com/forum/index.php?topic=1487.0)
> 
I think I have had a similar problem with PCLOS in the past. IIRC the solution was as follows.

Open Synaptic
Click on "Custom" bottom left.
Select "Broken" in LH panel.
There will probably be a package shown in the main panel with a red square next to it. This is the package that is causing the problem.
Click the red square, it should turn white.
Do your update or install or whatever you want.

The problem may well appear again next time you use use Synaptic, if so try to uninstall the problem package.

Hope this helps.

Richard.
	


---

