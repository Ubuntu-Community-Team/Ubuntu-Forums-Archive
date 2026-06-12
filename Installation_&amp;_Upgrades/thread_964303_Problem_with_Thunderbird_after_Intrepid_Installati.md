---
title: "Problem with Thunderbird after Intrepid Installation"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by rudeboyskunk on 2008-10-30
Ok, so I did this when I installed Hardy, and it worked just fine.  What I did was copy the "Mail" folder from my .mozilla-thunderbird folder to my portable hard drive, and then, after doing a clean install of Intrepid, I copied the "Mail" folder back to the brand new .mozilla-thunderbird folder.  However, this time around, it does not automatically load all the emails and settings.  What went wrong?

---

### Post by rudeboyskunk on 2008-10-30
*bump*

---

### Post by Ng Oon-Ee on 2008-10-30
The 'Mail' folder for Thunderbird does not contain all the data for your Thunderbird Profile (that's the word used by the Mozilla line of applications, Firefox and Thunderbird being the 2 most popular).

Within your .mozilla-thunderbird folder (or wherever you keep your profiles) you would have seen a folder with some alphanumerical name (8xs9awhd.....). Inside this folder was your 'Mail' folder, which ONLY contains your email, and some other files, which contain your extensions, your account settings (losing these can be a pain) etc. etc.

So the obvious solution WAS to copy the entire profile folder (the one with the wierd name). If you don't have it at hand now, then I'm afraid you have to set up your account as it was before, then copy your 'Mail' folder over to your new profile.

If you haven't just copied the 'Mail' folder but also the entire profile folder, there's a profile.ini folder within .mozilla-thunderbird which needs to point to the profile folder you want to use. The easier way to change this instead of editing it is by running 'thunderbird -P' in the terminal to call up the profile manager and creating a new profile which points to the folder you wish to use.

Let me know if there's anything you need help with.

---

