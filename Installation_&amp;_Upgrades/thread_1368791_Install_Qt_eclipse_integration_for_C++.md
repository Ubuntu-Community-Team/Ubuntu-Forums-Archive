---
title: "Install Qt eclipse integration for C++"
date: 2009-12-31
forum: Installation &amp; Upgrades
---

### Post by zbenta on 2009-12-31
Hello,

Can anyone give me a hand on this one?
I've followed all the tutorials online that show how to integrate QT with eclipse and I can't get it to work.
I've installed Eclipse from using synaptics then in Eclipse I go to Help->Install new Software and add the link [http://download.eclipse.org/tools/cdt/releases/galileo](http://download.eclipse.org/tools/cdt/releases/galileo)
I then choose the CDT to be installed, it goes perfectly and then I download [http://qt.nokia.com/developer/eclipse-integration](http://qt.nokia.com/developer/eclipse-integration) and untar it to /usr/lib/ .
Then all the tutorials tell me to go to Window -> Preferences -> QT and insert the Path to my QT instalation.
I've tried it but I cant seem to Have the QT option on the Window -> Preferences in Eclipse.
I also tried to run the build.sh script, that comes with the Qt integration downloaded from nokia, to see if i could compile the plugins and then move the jar files to the /usr/lib/eclipse/plugins/ directory, I also failed to do this.
Can anyone give a hand on this one?

---

### Post by zbenta on 2010-01-05
I've installed the QT Creator IDE and tried following the Mythhello plugin guide ( [http://www.mythtv.org/wiki/Building_Plugins:HelloMyth](http://www.mythtv.org/wiki/Building_Plugins:HelloMyth)
the problem that I'm having is that I can't get the mythhello plugin to build because it tells me I'm missing some header files.
I installed libmyth-dev using synaptics and still it didn't work.
Has anyone got a solution for me?
How can I get the latest libmyth-dev files, would this be a possible solution?

---

### Post by leo.demiurg on 2010-04-03
> **zbenta said:**
> 
I then choose the CDT to be installed, it goes perfectly and then I download [http://qt.nokia.com/developer/eclipse-integration](http://qt.nokia.com/developer/eclipse-integration) and untar it to **/usr/lib/** .


Hi.
Try to untar eclipse-integration plugin to .eclipse subdirectory of your home directory, not to /usr/lib/. This should help.

---

