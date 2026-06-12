---
title: "Upgrading/Fresh install soon. A few questions."
date: 2022-12-27
forum: Installation &amp; Upgrades
---

### Post by 77_GCSX on 2022-12-27
After putting off going from 16.04 to the latest version the fresh install is in sight, probably a week or 2 at the most.

I have a couple items I'd like to ask about. 
#1 - I play Minecraft. It's an older version (1.7.2) but it's modded and I just like the way it is set up.
#2 - Thunderbird...Migrating all "boxes" (In, Sent, etc...)

Regarding items #1 and 2 - Can I just copy the pertinent folders/files from my 16.04 Home folder to the new Home folder and have everything I need to keep going? For example: the game folder from old Home to new Home in the same place, Java folder from old Home location to new Home location?

As far as Thunderbird I've researched how to "move" from one computer to another so I'm 99% sure this won't be a problem.

If anyone has any info or ideas just let me know.

Thank You (and looking forward to the new Ubuntu!!)

---

### Post by oldfred on 2022-12-28
Do not know about Minecraft.

But i have used same Thunderbird profile for years thru many installs.
I have shared profile across different installs on same system by having it in a data partition. 
I used to do the same with Firefox but now that is not really working. And now it is version specific where years ago I could use it with slightly older or newer version. 

I typically have to start Thunderbird so it writes a new profile. Then I copy my profile & profile.ini or edit profiles.ini in .thunderbird folder. 
I assume Thunderbird will have an update where it becomes more like Firefox, so I make sure I backup profile regularly. 

thunderbird:
[https://support.mozilla.org/en-US/products/thunderbird](https://support.mozilla.org/en-US/products/thunderbird)
[https://support.mozilla.org/en-US/kb/moving-thunderbird-data-to-a-new-computer](https://support.mozilla.org/en-US/kb/moving-thunderbird-data-to-a-new-computer)
[https://support.mozilla.org/en-US/kb/profiles-where-thunderbird-stores-user-data](https://support.mozilla.org/en-US/kb/profiles-where-thunderbird-stores-user-data)
[http://kb.mozillazine.org/Thunderbird_:_FAQs_:_Changing_Profile_Folder_Location](http://kb.mozillazine.org/Thunderbird_:_FAQs_:_Changing_Profile_Folder_Location)

---

### Post by guiverc on 2022-12-28
I have no idea about minecraft so can't help there.
For thunderbird I'd take OldFred's advice; I have nothing useful there either.

I have a Ubuntu Desktop 16.04 LTS system I've been meaning to upgrade for years now, in my case it's used as an *offline *media player, and *rarely* so I'm in no hurry (*it's mouse needs batteries & has been waiting for two years now for them*).

In my case I plan on an *upgrade via re-install *(that's not an official name, just what I like calling it; Lubuntu calls it *Install using existing partition* where it's described [here]("https://discourse.lubuntu.me/t/testing-checklist-understanding-the-testcases/2743") for QA-testers), but I've still not decided what to upgrade it too as I don't want GNOME (*what Ubuntu Desktop now is*) & haven't selected my preferred flavor for that box.

That's a re-install **without format**of the new release using the same partitions. It'll take note of your installed packages, erase system directories, then install new system from installation.media, then **if** internet is available download & re-install the *manually installed* packages **where** they are available for your new release from Ubuntu repositories. On completion you are asked to reboot as per normal after an install.

That install type is intended (& QA-tested) for Ubuntu repository packages only, ie. not 3rd party. It can work with some 3rd party too, but errors are expected and if prompted to file a bug report over 3rd party packages - I'll suggest don't (*they're not supported*).  If I get error messages from the 3rd party packages, I just note them so I can re-install those myself post-install.

Minecraft I believe is 3rd party; why I'm trying to stress the third party with this method, but if it was me I'd try this install first. The install method official was intended for REPAIR purposes with the same release, but there is nothing done to prevent a different release being installed allowing the '*upgrade via re-install*' as I'm describing here.  (*with 23.04 we'll hopefully see the return of the Repair option on the installer menu like we had more than a decade ago.. instead of us manually triggering the install ourselves as I'm suggesting here*)

OF COURSE - ensure you have GREAT BACKUPS before you start.

If the '*upgrade via re-install*' fails, you can always do a *clean* install & you'll only lose some time with having tried this first. I use this method >50 times per year (*mostly in QA*) jumping around releases rather regularly on some installs, and love testing this as my 'new' install starts with my music & playlists having survived & thus can be used as a evaluate that 'new' install.

Key step though is have good backups.  It's easy to make mistakes  *(and I'm speaking from experience here*).

QA = *Quality Assurance*

---

