---
title: "[SOLVED] Lotus Notes 8 on Gutsy (7.10)"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by SpaceTeddy on 2007-10-24
Hi Everyone,

I am currently trying to get lotus notes 8 final release working on my laptop here. The file i used for installing was C152AML directly downloaded from IBM. 

**== what i have done ==**
So after that was done, i extracted the installer, switched to safe mode (no xgl or compiz since that messes with the display of the install shield) and installed with gksu/sudo. everything worked fine, and i was really excited here. First try, and it is acctually installing without me tweaking anything.
The installer finished normal, and i had a little button in my Application menu called "lotus notes 8". Being bold, i acctually clicked that entry, to be greeted by a "permission denied". After a short search i found the /opt/linux/lotus/notes only being readable by root... so i changed that to be world readable - even gave the notes executable the x flag so i can run it. Then i started it again - and here we go...

**== My Problem ==**
the splashscreen showed... then notes showed... and got stuck. Usually there sould be a user setup now... but the notes window just stays frozen until i kill it. I've tried pretty much everything i can think by now, but the setup won't show... notes just freezes before the user starts. (no CPU usage either - it just sits there until i kill it)

Does anyone know why this is the case ? or does anybody have a solution to this problem ?

thanks in advance for reading this

PS: i am using a fresh gutsy install with my old home-dir from feisty. But  i think i removed everything notes-related from my home-dir (except the id's)

---

### Post by mrtom852 on 2007-10-24
Hi,

I found it best to run Notes 8 from a shell to start with. It reports any missing libraries that you may need to install.
I've been running it under KDE on Debian and compiled a list of dependencies [[COLOR="Red"]here[/COLOR]]("http://blog.nominet.org.uk/tech/2007/09/20/lotus-notes-8-on-debian/")

Good luck!

Tom

---

### Post by SpaceTeddy on 2007-10-24
Thanks for the reply... i've checked all the dependencies (had them all installed) set the Enrviroment and created the softlink - no luck.

here is what notes says when i run it in the console:

> 2007/10/24 22:37:11.238 KONFIGURATION eclipse.buildId=build20070821-1029
java.fullversion=J2RE 1.5.0 IBM J9 2.3 Linux x86-32 j9vmxi3223ifx-20070714 (JIT enabled)
J9VM - 20070713_13151_lHdSMR
JIT  - 20070109_1805ifx5_r8
GC   - 200701_09
BootLoader constants: OS=linux
, ARCH=x86
, WS=gtk
, NL=de_DE

Framework arguments:  -dir ltr -personality com.ibm.rcp.platform.personality -product com.ibm.notes.branding.notes -plugincustomization /opt/ibm/lotus/notes/framework/rcp/plugin_customization.ini
Command-line arguments:  -os linux -ws gtk -arch x86 -dir ltr -personality com.ibm.rcp.platform.personality -product com.ibm.notes.branding.notes -data /home/ipoese/lotus/notes/data/workspace -plugincustomization /opt/ibm/lotus/notes/framework/rcp/plugin_customization.ini ::class.method=com.ibm.rcp.core.internal.logger.frameworkhook.writeSession() ::thread=main ::loggername=com.ibm.rcp.core.internal.logger.frameworkhook


that does not make a whole lot of sense to me... but it does not look like something is mittion... or am i mistaken there ?
after that, the notes window comes up and freezes.

when i kill it i get the folling error:
> JVM terminated. Exit code=1
/opt/ibm/lotus/notes/framework/rcp/eclipse/plugins/com.ibm.rcp.j2se.linux.x86_1.5.0.SR4-200708211029/jre/bin/notes2w
-Xmx512m
-Xquickstart
-Xjit:noResumableTrapHandler
-Dosgi.framework.extensions=com.ibm.rcp.core.logger.frameworkhook,com.ibm.cds
-Xscmx64m
-Xshareclasses:name=xpdplat%g,groupAccess,keep,nonfatal
-Drcp.home=/opt/ibm/lotus/notes/framework
-Drcp.data=/home/ipoese/lotus/notes/data/workspace
-Dosgi.splashPath=platform:/base/../shared/eclipse/plugins/com.ibm.notes.branding,platform:/base/../shared/eclipse/plugins/com.ibm.notes.branding.nl1,platform:/base/../shared/eclipse/plugins/com.ibm.notes.branding.nl2,platform:/base/../shared/eclipse/plugins/com.ibm.notes.branding.nl3
-Dcom.ibm.rcp.install.id=1193228828289
-Drcp.install.config=multiuser
-Declipse.registry.nulltoken=true
-Dautopd.logfile.generations=3
-Dorg.apache.xerces.xni.parser.XMLParserConfiguration=org.apache.xerces.parsers.XIncludeAwareParserConfiguration
-Dautopd.instance.area=/home/ipoese/lotus/notes/data/workspace/autopd/
-Disa.ignoreESR=true
-Djava.util.logging.config.class=com.ibm.rcp.core.internal.logger.boot.LoggerConfig
-Dcom.ibm.pvc.webcontainer.port=0
-Disa.ignorePortableCollector=true
-Disa.ignoreFeedback=true
-Disa.ignoreUpdate=true
-Dderby.stream.error.file=/home/ipoese/lotus/notes/data/workspace/logs/derby.log
-Djava.security.properties=file:/opt/ibm/lotus/notes/framework/rcp/eclipse/plugins/com.ibm.rcp.base_6.1.1.200708211029/rcp.security.properties
-Djava.protocol.handler.pkgs=com.ibm.net.ssl.[www.protocol](www.protocol)
-Dosgi.hook.configurators.exclude=org.eclipse.core.runtime.internal.adaptor.EclipseLogHook
-Drcp.osgi.install.area=/opt/ibm/lotus/notes/framework/eclipse
-Xbootclasspath/a:/opt/ibm/lotus/notes/framework/rcp/eclipse/plugins/com.ibm.rcp.base_6.1.1.200708211029/rcpbootcp.jar
-jar /opt/ibm/lotus/notes/framework/rcp/eclipse/plugins/com.ibm.rcp.base_6.1.1.200708211029/launcher.jar
-os linux
-ws gtk
-arch x86
-launcher /opt/ibm/lotus/notes/framework/rcp/eclipse/plugins/com.ibm.rcp.base_6.1.1.200708211029/linux/x86/eclipse
-name IBM Lotus Notes
-showsplash 600
-exitdata 518020
-nl de_DE
-dir ltr
-personality com.ibm.rcp.platform.personality
-product com.ibm.notes.branding.notes
-data /home/ipoese/lotus/notes/data/workspace
-configuration /home/ipoese/lotus/notes/data/workspace/.config
-plugincustomization /opt/ibm/lotus/notes/framework/rcp/plugin_customization.ini
-vm /opt/ibm/lotus/notes/framework/rcp/eclipse/plugins/com.ibm.rcp.j2se.linux.x86_1.5.0.SR4-200708211029/jre/bin/notes2w
-vmargs
-Xmx512m
-Xquickstart
-Xjit:noResumableTrapHandler
-Dosgi.framework.extensions=com.ibm.rcp.core.logger.frameworkhook,com.ibm.cds
-Xscmx64m
-Xshareclasses:name=xpdplat%g,groupAccess,keep,nonfatal
-Drcp.home=/opt/ibm/lotus/notes/framework
-Drcp.data=/home/ipoese/lotus/notes/data/workspace
-Dosgi.splashPath=platform:/base/../shared/eclipse/plugins/com.ibm.notes.branding,platform:/base/../shared/eclipse/plugins/com.ibm.notes.branding.nl1,platform:/base/../shared/eclipse/plugins/com.ibm.notes.branding.nl2,platform:/base/../shared/eclipse/plugins/com.ibm.notes.branding.nl3
-Dcom.ibm.rcp.install.id=1193228828289
-Drcp.install.config=multiuser
-Declipse.registry.nulltoken=true
-Dautopd.logfile.generations=3
-Dorg.apache.xerces.xni.parser.XMLParserConfiguration=org.apache.xerces.parsers.XIncludeAwareParserConfiguration
-Dautopd.instance.area=/home/ipoese/lotus/notes/data/workspace/autopd/
-Disa.ignoreESR=true
-Djava.util.logging.config.class=com.ibm.rcp.core.internal.logger.boot.LoggerConfig
-Dcom.ibm.pvc.webcontainer.port=0
-Disa.ignorePortableCollector=true
-Disa.ignoreFeedback=true
-Disa.ignoreUpdate=true
-Dderby.stream.error.file=/home/ipoese/lotus/notes/data/workspace/logs/derby.log
-Djava.security.properties=file:/opt/ibm/lotus/notes/framework/rcp/eclipse/plugins/com.ibm.rcp.base_6.1.1.200708211029/rcp.security.properties
-Djava.protocol.handler.pkgs=com.ibm.net.ssl.[www.protocol](www.protocol)
-Dosgi.hook.configurators.exclude=org.eclipse.core.runtime.internal.adaptor.EclipseLogHook
-Drcp.osgi.install.area=/opt/ibm/lotus/notes/framework/eclipse
-Xbootclasspath/a:/opt/ibm/lotus/notes/framework/rcp/eclipse/plugins/com.ibm.rcp.base_6.1.1.200708211029/rcpbootcp.jar
-jar /opt/ibm/lotus/notes/framework/rcp/eclipse/plugins/com.ibm.rcp.base_6.1.1.200708211029/launcher.jar

but no luck running it... any other idea what the problem might be ?

---

### Post by mrtom852 on 2007-10-25
I can't see any errors there either. The next line that my installation prints is

25/10/2007 07:58:08   Lotus Notes client started

:-)


A colleague of mine did have a similar problem where he wasn't able to reload Notes without 'rebooting'. We never worked out what temporary files were lying around though. I guess you could try deleting your ~/lotus directory to see if it will re-create it.

You might also find more users at the notes 8 forum - [http://www-10.lotus.com/ldd/nd8forum.nsf](http://www-10.lotus.com/ldd/nd8forum.nsf)

---

### Post by hgaerttner on 2007-10-27
Tried to install it several times and ran into the same error all time.
The installation process works fine (at least I don't get any errors here). Even the icons are there immediately.

I followed the reccomended procedures to make the directories available for my user account but when I try to start Notes I get this error:

[B]Could not launch menu item
Failed to execute child process "/opt/groupware/ibm/lotus/notes/framework/../notes" (No such file or directory)[/B]

The interesting fact is that I can start Lotus Documents, Spreadsheets and Presentations without problems. Looks like only an important part for the notes client is missing.

Oh, and I'm running Ubuntu on a virtual machine (Parallels 2.2) - but I don't think that sould make a difference.

Using the uninstall process it says "uninstalled correctly" and most files and the menu icons are gone but some directories are left.
So has anyone found informations were to look and maybe delete some left directories and files for a real cleanup? I'n not as experiencec in Ubuntu ... so is the somthing similar to the registry in Windows that has to be cleaned or otherwise could be the reason for my problems as my first install was a failure and my have left some unwanted information?


EDIT:
Corrupt uninstall was indeed the reason. I had to delete the installshield directory manually ... after that it worked.

Thanks
Harald

---

### Post by kimmey2k3 on 2007-10-31
I had the same problem and I only DISABLED the desktop effects and it worked perfectly! Try that

---

### Post by SpaceTeddy on 2007-10-31
just went into the safe mode of gnome (no effects - nothing) and started notes there... but that did not help either... so still no luck

as for removing the install files - yes, i did that aswell - no luck
@hgaerttner: that error looks like notes forgot to the set executable flag in the main notes file - but then, i did not install all that extra stuff from notes, since i like openoffice more. 

unforteunatly my notes still doesn't let me in...

---

### Post by Squench on 2007-10-31
The way I got notes to work was to install without compiz. Once installed I had to chown the four directories it creates. 1. /etc/ibm 2. /etc/lotus 3. /home/"usr"/lotus 4. /opt/ibm
After that it worked great even with compiz running. I hope this helps somewhat.

---

### Post by SpaceTeddy on 2007-10-31
ok, THAT got my attention - and it works now - i never chowned the /opt/ibm path to me, since that is undesired behavior in my opinion. For testing, i just did that now - and here we go - notes started all the way.

I am not a big fan of giving anything to a user besides their own directory, so i created a group notes, chgrp'd the /opt/ibm folder (only ONLY that) to it and set the group to write access to the file by 
chgrp g+w /opt/ibm -R 
(why ever notes needs to WRITE anything there is beyond me - i always thought that is what /tmp is for... anyway)

added myself to the group and then restarted the x-server - voilá - notes works now.

Thank you everyone for contributing to this problem.

---

### Post by fatbuttlarry on 2008-02-16
The blank screen option seems to be a bazaar java GUI bug.  I recognized it because I saw it before with other applications that use java installers (Such as Squirrel SQL).

I had good luck by using kwin as the window manager.

[http://ubuntuforums.org/showthread.php?p=4268844](http://ubuntuforums.org/showthread.php?p=4268844)

Search for "Issue #1: Unreadable Installer GUI:", and it will have the work-around steps.

-Tres

---

