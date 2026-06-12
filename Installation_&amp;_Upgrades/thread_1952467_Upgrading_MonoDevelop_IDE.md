---
title: "Upgrading MonoDevelop IDE"
date: 2012-04-04
forum: Installation &amp; Upgrades
---

### Post by hpng on 2012-04-04
I now have monoDevelop version 2.4on Ubuntu 11.04. I went to Ubuntu Software Center and Synaptic Package manager, and I do not see a way for me to update monoDevelop from 2.4 to 2.8 ( the latest version).  How do I go about getting Ubuntu to automatically update a new version of Mono Develop from here: [http://monodevelop.com/Download](http://monodevelop.com/Download)  If I remove current monoDevvelop version 2.4, then how do I setup Ubuntu Software Center or Synaptic package manager to dowload MonoDevelop?  thanks.

---

### Post by directhex on 2012-04-04
> **hpng said:**
> I now have monoDevelop version 2.4on Ubuntu 11.04. I went to Ubuntu Software Center and Synaptic Package manager, and I do not see a way for me to update monoDevelop from 2.4 to 2.8 ( the latest version).  How do I go about getting Ubuntu to automatically update a new version of Mono Develop from here: [http://monodevelop.com/Download](http://monodevelop.com/Download)  If I remove current monoDevvelop version 2.4, then how do I setup Ubuntu Software Center or Synaptic package manager to dowload MonoDevelop?  thanks.

With difficulty. MonoDevelop 2.6+ requires .NET 4.0 support (Mono 2.8+) which is not available on Ubuntu 11.04.

I'd suggest upgrading or downgrading your distro. 2.8 is part of Ubuntu 12.04, and I produce backports for Ubuntu 10.04.

---

### Post by hpng on 2012-04-04
Dear Directhex:

> With difficulty. MonoDevelop 2.6+ requires .NET 4.0 support (Mono 2.8+) which is not available on Ubuntu 11.04.

I'd suggest upgrading or downgrading your distro. 2.8 is part of Ubuntu 12.04, and I produce backports for Ubuntu 10.04.

thanks for reply.
Now I am new to Linux, just a user but not heavy into Linux OS or development.
So this is my first try.

I am not sure what the above means.  Here is my situation.  I am using Visual studio 2010 to do some C# coding .  My Ubuntu is 11.04.  I set my target framework to .NET 3.5 since my monoDevelop IDE has runtime version mono / 3.5 .NET support from the built options window.

So I copy entire Winform project created in Visual Studio into  Ubuntu 11.04.
I was able to built and run the application, BUT I also got a [COLOR=DarkOrange]RED[/COLOR] higlighted node inside Reference node like this:
MyFirstProject->Reference->[COLOR=DarkOrange]System.Deployment[/COLOR] -> [COLOR=Magenta]**Assembly Not Available for Mono / .NET 3.5 ( in mono 2.6.7 ).**[/COLOR]

However, I was able to run the application, and so far it works.  :p
***[COLOR=Blue]So why do I have System.Deployment Assembly Not Available warning?[/COLOR]***

About this:

 "With difficulty. MonoDevelop 2.6+ requires .NET 4.0 support (Mono 2.8+) which is not available on Ubuntu 11.04"

Knowing my situation:  usinng Visual Studio 2010 and then mving the projects to MonoDevelop.......
is it better that I upgrade to MonoDevelop 2.6+........ i.e Ubuntu 12.04?
My current MonoDevelop IDE version is 2.4 on Ubuntu 11.04. 
If so, is there a way to upgrade from 11.04 straight to 12.04?
It seems the Ubuntu upgrade manager only do one upgrade stage at at time, so I will have to do several upgrade, a very long time before I get to Ubuntu 12.04.

"I'd suggest upgrading or downgrading your distro. 2.8 is part of Ubuntu 12.04, and I produce backports for Ubuntu 10.04"

Please explain what **backports **means?

Thanks for all the help....

---

### Post by directhex on 2012-04-05
> **hpng said:**
> Dear Directhex:



thanks for reply.
Now I am new to Linux, just a user but not heavy into Linux OS or development.
So this is my first try.

I am not sure what the above means.  Here is my situation.  I am using Visual studio 2010 to do some C# coding .  My Ubuntu is 11.04.  I set my target framework to .NET 3.5 since my monoDevelop IDE has runtime version mono / 3.5 .NET support from the built options window.

So I copy entire Winform project created in Visual Studio into  Ubuntu 11.04.
I was able to built and run the application, BUT I also got a [COLOR=DarkOrange]RED[/COLOR] higlighted node inside Reference node like this:
MyFirstProject->Reference->[COLOR=DarkOrange]System.Deployment[/COLOR] -> [COLOR=Magenta]**Assembly Not Available for Mono / .NET 3.5 ( in mono 2.6.7 ).**[/COLOR]

However, I was able to run the application, and so far it works.  :p
***[COLOR=Blue]So why do I have System.Deployment Assembly Not Available warning?[/COLOR]***

System.Deployment is not implemented in Mono, and is not available.

> About this:

 "With difficulty. MonoDevelop 2.6+ requires .NET 4.0 support (Mono 2.8+) which is not available on Ubuntu 11.04"

Knowing my situation:  usinng Visual Studio 2010 and then mving the projects to MonoDevelop.......
is it better that I upgrade to MonoDevelop 2.6+........ i.e Ubuntu 12.04?

If you intend to target .NET 4.0, you need Mono 2.8+, so need Ubuntu 11.10 or above.

> My current MonoDevelop IDE version is 2.4 on Ubuntu 11.04. 
If so, is there a way to upgrade from 11.04 straight to 12.04?
It seems the Ubuntu upgrade manager only do one upgrade stage at at time, so I will have to do several upgrade, a very long time before I get to Ubuntu 12.04.

That upgrade path is not tested. The only tested paths are "regular release" upgrades e.g. 11.04->11.10, and "LTS upgrades" e.g. 10.04->12.04. No testing is done on other jumps - it may work, it may not.

> "I'd suggest upgrading or downgrading your distro. 2.8 is part of Ubuntu 12.04, and I produce backports for Ubuntu 10.04"

Please explain what **backports **means?

Thanks for all the help....

Linux distributions release with specific, tested versions of all the software in the repositories - in this case, Mono 2.6.7 and MonoDevelop 2.4. Occasionally, newer versions of software can be taken from newer versions of a distribution, and be made available in an older distribution - i.e. ported backwards from a newer distribution. Hence "backported"

---

