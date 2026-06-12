---
title: "Lost Thunderbird Calendar"
date: 2013-10-30
forum: Installation &amp; Upgrades
---

### Post by SpikeLS6 on 2013-10-30
One of the recent Updates either moved or deleted my Thunderbird Profiles. When I bring up the Calendar (Lightning), I get a blank grid with no information and no taskes.

I made a new Profile in Terminal with suggestions from the Forum, but now I can not get back to the original Profile with all the Email addresses, etc. How do I get back to my original Thunderbird Profile even if I have to give up the Lightning Calendar?

Spike

---

### Post by ajgreeny on 2013-10-30
This is a problem of the most recent version of lightning but not the same version of TB.  I did not notice it but there is a note at the Thunderbird add-ons site
> If you are using Linux, be sure to use the **exact version combination**:
Thunderbird 24.0: Lightning 2.6
Thunderbird 24.0.1: Lightning 2.6.1
Thunderbird 24.1.0: Lightning 2.6.2
You have probably updated the lightning calendar version to 2.6.1 as I had, and it will not work with TB 24, only with TB 24.0.1.

Go to [https://addons.mozilla.org/thunderbird/downloads/file/227472/lightning-2.6-tb+sm-linux.xpi?src=version-history](https://addons.mozilla.org/thunderbird/downloads/file/227472/lightning-2.6-tb+sm-linux.xpi?src=version-history) and you will get the 2.6 version which you can install from the **Tools ->Add-ons** manager.  I removed lightning 2.6.1 first but I don't know if it is necessary to do that.

What did you do to get a new profile?  I hope you did not delete the old hidden .thunderbird folder in your home or you will have lost everything.

---

### Post by vanadium on 2013-10-30
Do not forget to turn off automatic updates of addons, or you will have 2.6.1 back in a few days.

---

### Post by ajgreeny on 2013-10-30
I wonder if the problem has arisen because I added the most updated version of lightning from the TB Add-ons website and not through the ubuntu repos for 12.04.  Perhaps the repository version keeps pace with the TB version and does not always use the most recent.

PS:
@ vanadium

How does one turn off automatic updating of add-ons?  I can see how to stop checking for updates, but I think you can still choose not to update even if TB tells you an update for lightning is available, but I can not see any way that allows updating without first being told and then choosing to do so.

---

### Post by vanadium on 2013-10-31
That's it probably. I also usually install the addon through thunderbird, but I recently was aware that it can also be installed from within the Ubuntu software center. Edit - Preferences - Advanced, Updates tab to turn automatic updating of addons off.

---

### Post by Bill Tetzeli on 2013-10-31
If you've downloaded the most recent Ubuntu updates, including updating Thunderbird to 24.1.0, uninstall and then reinstall Lightning from Add-ons in the Tools menu.  It should reinstall to the latest version of Lightning, which will be compatible.

To be clear, here's what I did:

Ran "sudo apt-get install thunderbird" to update to 24.1.0
Opened Thunderbird, selected Tools > Add-Ons
Clicked the Extensions tab
Removed Lightning
Reinstalled Lightning
Restarted Thunderbird

Both my email and calendar data were untouched throughout the entire process.  All is as it was before, calendar's back to being fully functional.  Hope this helps. :-)

---

### Post by SpikeLS6 on 2013-10-31
All your suggestions are good, but I find that I am back to my original problem. I used:

"The local user configuration/profile may be the cause of problems.
This is not removed or modified when you remove/reinstall programs. 
The location for thunderbird is ~/.mozilla-thunderbird
My advice is to reboot, open terminal, and launch thunderbird with this command:
 	Code:
 	thunderbird -ProfileManager 
Thunderbird-Choose User Profile
Click** Create Profile...** button
Leave the old profile for now.
Double click the new profile or highlight and click Start Thunderbird button.
You're starting with a clean slate,all servers and settings must be reconfigured.
No plugins/addons are installed.
Lightning is beta software."

The new Profile is there, but with no link to my original Profile file. I have used CD to try to get to "~/.mozilla-thunderbird", but can not access either the original Profile or the New 'clean slate'One.

Somehow I think I need to get my original profile returned before I can continue with these suggestions to match Versions.

Any ideas?

Spike

---

### Post by ajgreeny on 2013-10-31
The new 24.1 version of TB only arrived in the repos for 12.04 today, so I have now updated to that and will see if the newer version of lightning also works when I update that.
EDIT:
Yes, everything is OK again with TB 24.1 and lightning 2.6.2

---

### Post by billcauley2 on 2013-10-31
Got 24.1.0 and Lightning 2.6.2 this morning, and it "works" with the problems that the synchronization with Google Calendar produces incorrect times and dates for events.  Times are off by seven hours, deleted events are still showing in Lightning, and some events have changed days. Also, the month calendar that used to appear in Events is no longer.  Guess a fix will be coming along soon...

---

### Post by SpikeLS6 on 2013-10-31
I found the .thunderbird Folder in my Home tree, but the only Profile in it is the new one I created. Apparently the old one got deleted, although I did not see anything when I made the new Profile that would prevent having the old one and the new one. Apparently two can not be selected individually. Is that true? If so, then I have lost all the email addresses and will revert to using a hard copy Day-Timer. My new T-Bird is 24.1.0, and the new Lightning is 2.6.2.

Please let me know if I have no other alternatives and I will stay with the new profile and format this Thread as Solved.

Thank you for your help

Spike

---

### Post by ajgreeny on 2013-10-31
Look more deeply in that .thunderbird folder and you may find two profiles, both starting with random but different 8 character alphanumeric string.  One will be x#x#x#x#.**default** the other will be x#x#x#x#.**newname**, newname being whatever you called the new profile when you made it.  Highlight the new profile folder and then hit delete which will simply put it in the wastebasket.  Now start thunderbird again and you may miraculously find that your old profile is all that is available for TB to use and all your old mail, contacts, etc etc are still there.

---

### Post by SpikeLS6 on 2013-10-31
I did indeed find two Profiles as you suggested in the .thunderbird Folder. I deleted the new I made with the same name I used to make it. However, after rebooting T-Bird, then rebooting the whole PC, T-Bird will not come up and gives me an error of "Profile Missing; Your thunderbird profile can not be loaded. It may be missing or inaccessible. The file name of the Default Profile is: uivcg0kz.default. Is there a way somewhere in T-Bird's Options or Preferences to point to this file?

With both T-Bird at 24.1.0 and Lightning at 2.6.2, getting this .default file would solve my problem.

Thank you.

Spike

---

### Post by SpikeLS6 on 2013-10-31
The .ini file is:

[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
Path=uivcg0kz.default

[Profile1]
Name=Michael
IsRelative=1
Path=sv43zeqc.Michael
Default=1


Should the [Profile1] be removed? What number should the "StartWithLastProfile=___ be?

Spike

---

### Post by ajgreeny on 2013-10-31
I'm on an android tab at the moment but I'll look tomorrow morning for a default .INI file.

---

### Post by SpikeLS6 on 2013-11-01
I have it solved. I deleted the [Profile1] in the .ini file. That left only the [Profile0] Default file, saved it, and started Tunderbird. After a couple of seconds, it began to load and checked all the Add-ons. Still no calendar, but T-Bird is up and running. I went into Tools/Add-ons and checked Lightning which proved to be the automatically updated 2.6.1. I Removed 2.6.1 and downloaded and installed 2.6.2. Bingo; complete calendar, Address Book, and Tasks were there minus the last three days of input.

Thank all you very much. I will get my entire hard drive backed up again pronto.

Spike

---

### Post by ajgreeny on 2013-11-01
For future reference, this is how to sort out the profiles if you get in this mess again.

There is no need to edit the profile.ini file as you can start TB with command **thunderbird -p** which will start the profile manager, which is how I assume you made the new profile.  From here you can delete the new profile you made, leaving you with just the one default.  At the moment you will still have the new profile folder in your hidden ~/.thunderbird folder, and this can now be deleted (the profile folder, not the whole .thunderbird folder).

---

### Post by SpikeLS6 on 2013-11-01
Thank you, AJ. You are exactly right on the creation of the new Profile. I appreciate the help you provided. It got me to thinking about the .ini file which helped solve my problem.

Spike

---

### Post by billcauley2 on 2013-11-02
Turns out the new Thunderbird doesn't pick up the system location as before.  It had to be set in the Lightning tab.  Still no calendar in the Events column though.

---

