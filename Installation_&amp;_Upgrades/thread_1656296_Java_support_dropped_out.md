---
title: "Java support dropped out?"
date: 2010-12-30
forum: Installation &amp; Upgrades
---

### Post by MAFoElffen on 2010-12-30
Ubuntu 10.10, Firefox 3.6.13, IceTea6 ext, Greasemonkey, Firebug, FlashBug...

Everything was going just great, then poof...  Firefox seems to have lost the ability to interpret java and javascript extensions.  It's strange, I have a javascript extension that I've used a lot in the last 2 to 3 months.  One night, was using- refreshed, gone.

Script was still there in GreaseMonkey, with all it's pointers to the web presence.  I have Google Chrome with the same extension and it stiill works fine.  Thought maybe it might be an install problem, so uninstalled/reinstalled Greasemonkey and the script//no change.  Uninstalled and reinstalled Firefox and extensions//no change.

I used Firebug to inspect element on a familiar web page where I inserted a table with imbedded javascript... doesn't execute any of the onclick processes on it.  This table "is" something that I have inserted on that same page previously with no problems and it executed those same onclick processes fine...

Which leads me to believe that somehow, in the past few weeks, I somehow lost the abilty to process java and javascript.  Could this be to soem recent updates or upstream changes?

Note-- I do have Eclipse IDE, JavaBeans IDE and Monkey Studio IDE installed on this instance of Ubuntu.  I've stayed with Ubuntu's flavor of the OpenJDK, instead of going to Sun's JRE in an attempt to stay open to future shifts and directions.

Any ideas anyone?

---

### Post by MAFoElffen on 2010-12-30
I should also probably add that there is not a problem with this in Win/Firefox.  This extension "was" (<--editted change) also working in Linux/Opera.  One noticable change is that when this extension was loaded previous to these problems... Firefow would have a popup bar come up to verifiy that I wanted to load this as an extension. Not any more...   Now it just displays the text of the .js file.

---

### Post by lovinglinux on 2010-12-30
[http://www.webgapps.org/firefox/general-troubleshooting](http://www.webgapps.org/firefox/general-troubleshooting)

---

### Post by MAFoElffen on 2010-12-31
Okay... Everything with Firefox "seems" to be okay.  I had moved this extension from Opera's Home\Documents\javascript\opera folder to tempoarily disable it... so I moved a copy of it back in to that directory... and it's not working there either.

Editting the html of pages and trying to embed javascript... fails now in FF and opeara, but works in chrome... but I believe that Firefox and Opeara use external Java Runtimes, while Chrome has it's own... 

](*,)THIS leads me to believe that my install of the OpenJDK runtime is somehow at fault, corrupt or no longer compatible some how.  Like I said, Pages with simple Embedded javascript "are not" working, even though preferences in my browsers "are" configured to use java.  

Currently for my java runtime environment, I'm using openjdk-6-jre.  (OpenJDK Java runtime, using Hotspot JIT), version 6b20-1.9.2-0ubuntu2.   Of course Sun Java's Test Page (@ java.org) does not work with this...  and says there is no java jre loaded at all...

What am I going to run into if I reinstall the OpenJDK runtime?  Or  should I just remove it and Install Sun's JavaJRE and see if that  corrects it?

Of course, then I have the 3 IDE's installed with their own Java Libs  and such... Which each have some type of jre requirements, right?

---

### Post by MAFoElffen on 2010-12-31
> 
What am I going to run into if I reinstall the OpenJDK runtime?

I reinstalled the openJDK packages and no resolution.  I remember seeing instructions for what packages of openJDK needing to be removed if Sun's javaJRE where installed "somewhere"...  I guess maybe that might be the next thing to try? 

I **really** wanted to stay with native Ubuntu packages. but there doesn't seem to be much interest in helping with this kind of problem.

---

### Post by MAFoElffen on 2010-12-31
Okay- Some progress.

I installed the Sun javadaJRE packages... still didn't help, but at least I could verify that java "was" working and what version it was compatible to.

I then went back to a terminal session and restepped through diagnosing Firefox.  When I started it with a "-P" option, I renamed my profile to "backup" and created a new "Default" profile.  Then everything started working again!!!  (At least java-wise)

But the session did come up with these errors:
```

mafoelffen@maf-ubuntu-01:~$ firefox -P
LoadPlugin: failed to initialize shared library libXext.so [libXext.so: cannot open shared object file: No such file or directory]
LoadPlugin: failed to initialize shared library /usr/lib/firefox-addons/plugins/libflashplayer.so [/usr/lib/firefox-addons/plugins/libflashplayer.so: wrong ELF class: ELFCLASS32]
Gtk-Message: Failed to load module "atk-bridge": /usr/lib/gtk-2.0/modules/libatk-bridge.so: wrong ELF class: ELFCLASS64
Gtk-Message: Failed to load module "atk-bridge": /usr/lib/gtk-2.0/modules/libatk-bridge.so: wrong ELF class: ELFCLASS64
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
shouldload: http://dfznew.byethost13.com/js/DFZWAssistant_gm.user.js
ignorescript: false
ignoring next script...
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Wrapper *** ERROR: NPP_Destroy() wait for reply: Connection reset by peer
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:2163):invoke_NPP_NewStream: assertion failed: (rpc_method_invoke_possible(plugin->connection))
Gtk-Message: Failed to load module "atk-bridge": /usr/lib/gtk-2.0/modules/libatk-bridge.so: wrong ELF class: ELFCLASS64
Gtk-Message: Failed to load module "atk-bridge": /usr/lib/gtk-2.0/modules/libatk-bridge.so: wrong ELF class: ELFCLASS64
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:1854):invoke_NPP_Destroy: assertion failed: (rpc_method_invoke_possible(plugin->connection))
*** NSPlugin Wrapper *** ERROR: NPClass::Invalidate() wait for reply: Connection reset by peer
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:1854):invoke_NPP_Destroy: assertion failed: (rpc_method_invoke_possible(plugin->connection))
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:1854):invoke_NPP_Destroy: assertion failed: (rpc_method_invoke_possible(plugin->connection))
mafoelffen@maf-ubuntu-01:~$ 

```
This instance of ubuntu has evolved from 9.04 thru 10.10.  I think some of these errors look like an old DVX or lfash driver from 9.04, that still seems to reside there.  (Right?)

I have a lot of saved passwords and bookmarks in an old DVX or flash file... that would be a long while to react from the blank file.  On correcting my main problem, are Firefox profile files editable?

---

### Post by MAFoElffen on 2010-12-31
I guess the question should now be= Where do I go from here?  

The problem is in the profile.  If I start from a fresh profile, I lose all my saved passwords and bookmarks.  If I go back to my old profile, I have all that, but have to find where in the profile directory I lost java support.

---

### Post by arpanaut on 2010-12-31
I had to recover from a corrupted profile recently and found this article helpful, at the bottom has info for recovering and working with profiles.

Hope this helps:   [http://support.mozilla.com/en-US/kb/Profiles#How_to_find_your_profile](http://support.mozilla.com/en-US/kb/Profiles#How_to_find_your_profile)

---

### Post by lovinglinux on 2011-01-01
> **MAFoElffen said:**
> I guess the question should now be= Where do I go from here?  

The problem is in the profile.  If I start from a fresh profile, I lose all my saved passwords and bookmarks.  If I go back to my old profile, I have all that, but have to find where in the profile directory I lost java support.

See [http://www.webgapps.org/firefox/fixing-corrupted-profiles](http://www.webgapps.org/firefox/fixing-corrupted-profiles)

---

### Post by ottosykora on 2011-01-01
java and javascrip are not the same, no java needed for simple javascript interperetation, so dont bother about java when it is just scripting on webpages what goes wrong. Tried to simply abck up bookmarks , remove browser completely and reinstall it again.
This would be my first try.


If you just do not see javascript on pages, you can export bookmarks, passwords can be exported too, cookies as well and java support is not important. 
So do not confuse the things, java is separate software, javascript included in your browser and works without any java installed.


and before changing anything, make also sure you have scripting enabled in preferences of your browser.

---

