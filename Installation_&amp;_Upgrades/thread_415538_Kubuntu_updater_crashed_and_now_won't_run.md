---
title: "Kubuntu updater crashed and now won't run"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by ngc on 2007-04-20
I started the upgrade to Feisty after opening Adept from the "updates available" icon in the system tray (I shut down everything else before starting the update, even knocking Amarok out of its usual position in the system tray). This seemed to be happily humming away installing the downloaded updates, and it was late, so I went to bed, intending to come back and look at the results in the morning.

Unfortunately, I came back to find 2 error dialogs displayed, but without the contents of any of the 3 windows (updater, first error dialog, second error dialog) actually painted on the screen. So I have absolutely no idea what went wrong on this initial execution (and web searching doesn't help, because the results I get for feisty upgrade issues are currently still saturated with discussions of the feisty beta).

However, now I get two strange behaviours from Adept. Firstly, if I ask it to fetch the list of updates, the "upgrade available" wizard appears again. For some reason, after clicking Finish on the wizard, nothing happens - Adept remains open, and the upgrader won't start. If I try launching Adept from a console window, there is no error message to indicate why the upgrader didn't start

After checking the recommended update guide on the Ubuntu forums, I decided to try the Full Upgrade button in Adept. How, this fails as soon as it gets to debconf, reporting a stack smashing error from perl (the modal error dialog in Adept means I can't easily copy and paste the error). For what it's worth, Adept indicates that my installed KDE version is 3.5.5.

Invoking apt-get upgrade directly managed to process a few more packages than Adept does, but this actually broke the updater even further: now it displays the file retrieval box for the release notes, but never actually displays them.

Not quite sure what my best course is from here - I have a variety of things set up for software development on this machine, and having to reconfigure a vanilla Kubuntu install would be quite a pain. Suggestions for how to find out more information about what went wrong, or how to get to a working Feisty installation greatly appreciated!

 [Update: I had a closer look at this, and don't know why it was ever considering debconf at all - Adept indicates I already have the latest version. I did notice, however, that po-debconf had an upgraded version available. I upgraded that package specifically (along with its dependencies), and now the full upgrade appears to be enjoying significantly greater success]

[Update2: Adept still ran into issues with completing the Full Upgrade (died trying to update kdm). However, a subsequent 'apt-get upgrade' appears to have fixed the various packages that were having problems. So it all looks pretty good now.]

---

