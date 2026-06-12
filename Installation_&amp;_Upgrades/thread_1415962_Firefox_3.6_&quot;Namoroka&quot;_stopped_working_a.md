---
title: "Firefox 3.6 &quot;Namoroka&quot; stopped working after recent update"
date: 2010-02-25
forum: Installation &amp; Upgrades
---

### Post by BASH-full on 2010-02-25
Firefox 3.6 "Namoroka" stopped working after a recent update.  Clicking on my panel launcher or the launcher in the applications menu does nothing.  I even tried  starting Firefox from the terminal and got an error message: "**(firefox-bin:3592): GLib-WARNING **: g_set_prgname() called multiple times**", whatever that means.

I would be willing to rip out Firefox and start all over again but I don't know how to remove the 3.6 version.  I couldn't find a method in the Software Center for doing that graphically.

Please help.

---

### Post by quixote on 2010-02-26
I had the same thing happen.  In my case the problem was that the update changed the shortcuts so that "firefox" no longer pointed to firefox.  To see whether there's an actual problem with your install you could use nautilus to go to the actual program, which is generally in (start from "Filesystem", not "Home") /usr/lib/firefox-3.6.your-version-number.  Double click "firefox" or "firefox.sh" and nautilus should ask you whether you want to display it, or run it.  Select run, and see if it starts.  If you still get errors, then the install is bad.  If it runs fine, then the shortcuts are bad, which is easy to fix if that turns out to be the problem.

As for uninstalling, it's just like the Good Old Days: all you have to do is delete the directory (eg /us/bin/firefox-3.6) and it's gone.  If you also want to get rid of all your previous settings, cache etc, those are in your home dir in a hidden .mozilla dir: /home/you/.mozilla/firefox/alphanumeric-jumble.default.  To see hidden files in nautilus, hit ctrl-h.

---

### Post by Arkitekt on 2010-02-26
I was having the same problem, turns out it is two different issues.

After some trial and error, I have discovered that the reason 3.6 won't start up is due to greasemonkey. The reason it is causing a problem with 3.6 is because greasemonkey seems to not auto-update when a new version comes out, most of us have pre-3.6 versions. I myself had a version from January of 2009. Looks like in 0.8.3 greasemonkey added a 3.6 compatibility flag. Updating manually from the add-ons website to 0.8.20100211.5 fixed this issue for me. 

I fixed my GLib warnings by downgrading libglib2.0-0 and libglib2.0-data to 2.22.1-0ubuntu1, the newest one from karmic-updates (2.22.3-0ubuntu1) seems to be unstable. For those wondering how to do this, in synaptic highlight the package and under the package menu on the toolbar select force version (CTRL-E).

Hope this solves this for everyone.

---

### Post by BASH-full on 2010-02-28
Never mind!  The situation resolved itself:p  I think an unspecified update fixed the problem.  Now I can go back to using FF again and ditch Opera.

Thank you for your suggestions, tho.  I learned some new things from your replies that I wasn't aware of before, like that I can "uninstall" a program just by deleting its folder.  That's heresy in the M$ world I usually inhabit!

---

### Post by quixote on 2010-02-28
Glad to hear it's sorted out!  Always kind of disturbing when you don't know what caused the problem . . . and then don't even know how it got solved!

It's M$'s Registry system, which I think was invented purely as an early form of DRM, that makes it so hard for the users to deal with their own programs.

---

### Post by manny43 on 2010-02-28
Did you upgrade firefox from Synaptic Package Manager?

---

### Post by tajreed on 2010-03-01
After recent upgrades, FF3.6 worked for several hours, then quit again. It will not open. There were new upgrades today, but still no luck. Xul runner was updated this am but had no effect.

Any ideas?

---

### Post by quixote on 2010-03-02
Try starting firefox from the command line.  Then you usually get a few error messages before it quits, which helps to figure out what's wrong.

---

