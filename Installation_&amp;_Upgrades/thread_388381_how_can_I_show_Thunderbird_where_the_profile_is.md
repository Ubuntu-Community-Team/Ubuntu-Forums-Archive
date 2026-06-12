---
title: "how can I show Thunderbird where the profile is?"
date: 2007-03-19
forum: Installation &amp; Upgrades
---

### Post by 1002285 on 2007-03-19
I have read a couple of howtos on that but they are not right for me, I think, because the folders and profile managers aren't in the places where they are supposed to be in these threads, etc.

I want to show mozilla-thunderbird in Ubuntu, that the profile is in another partition, not in the /home/username/.mozilla-thunderbird.

It did not start when I deleted the profile folder from that direction, although I had set the lines in the configuration file to refer to the right place. Now I have already removed thunderbird, but the profile is in the FAT32 partition. In Windows, the Thunderbird just started to work the right way after I set the folder locations in the account - server settings to that partition. But Ubuntu's Thunderbird said something like "thunderbird is already in use, close it", and startet to work when I copied the profile folder back to the old location.
I cannot find a place where to tell the thunderbird that the profile is not supposed to be where it thinks it should be.

What I have in the /home/username/.mozilla-thunderbird folder, is a profiles.ini file that looks like this (I did try to change the path like /partition-name/Mozilla....., but that did not help):

[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
Path=i893i6tb.default

And still an interesting addition:
I have removed thunderbird and installed it back. Now I changed the in this profile.ini file to
Path=/fat32-sda5/Mozilla_Profiles/Thunderbird/rsyfqtcl.default
but did not delete the profile folder from the /home/username/.mozilla-thunderbird
and I once more got the message about Thunderbird already running. Does this mean that Windows leaves something wrong in the profile directory when I close Thunderbird in Windows?

And the very same thing happened with firefox - when I changed the path in profiles.ini file to where I had copied the profile, it said - when trying to open Firefox - that it was already running. I don't understand anything anymore.

---

### Post by louis_nichols on 2007-03-19
OK. I'm not sure I understood all of your question(s), but here are my 2 cents on your problem(s). :)

First, where it says Path=Path=i893i6tb.default, you can give it an absolute path, like /home/username/etc... if you change the value of IsRelative to 0. So there you will have IsRelative=0.

Regarding the error "thunderbird is already in use, close it", that is likely caused by a previous crash or by your copying the profile folder while thunderbird was open and that didn't delete the lock file. In short, in your folder i893i6tb.default, you will find a file called *lock* which you should delete and then the app should start. If this still doesn't work, you should start just copying the relevant files to a different profile and starting anew, but still with the old info. Info about migrating profiles is [here]("http://kb.mozillazine.org/Migrating_settings_to_a_new_profile").

As a sidenote, here is a [howto on sharing your profile]("http://learn.clemsonlinux.org/wiki/Email:Sharing_your_Thunderbird_profile").

---

### Post by GeertPoels on 2007-03-19
U can always use to profile manager to create a location
[http://www.mozilla.org/support/firefox/profile](http://www.mozilla.org/support/firefox/profile)

Then overwrite it with the content of your old profile

---

### Post by 1002285 on 2007-03-20
thanks, guys, these were useful tips. I finally managed to run profile managers and point them to right locations in Windows and write the appropriate entries to profile.ini files in Linux.

---

