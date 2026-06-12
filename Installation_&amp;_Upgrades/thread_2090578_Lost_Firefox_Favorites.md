---
title: "Lost Firefox Favorites"
date: 2012-12-02
forum: Installation &amp; Upgrades
---

### Post by Gronknation on 2012-12-02
What happen was I downloaded the Wubi Ubuntu on my windows computer. The next thing you know my computer wont boot up. What I did was (with amazing help on this forum) Burn a CD (create Disk Image), boot from it, get to the desktop by 'Try  Ubuntu'.

Everything is there except my firefox favorites. For 99.9 percent of people favorites mean nothing. But to me they were SUPER important. I had 20+ amazing sites on there that blew my mind. They wouldn't impress an average person but I have tons of creative and awesome hobbies I do. #6 on my to do list was "go threw all firefox favorites". I have no idea the names of the sites and didn't plan to go on them until I got to it on my checklist.

I was also doing 3 projects and saved the pages I was on with them in my favorites bar. I was going threw 100's of pages. I would have no idea where I left off.

I feel positive though, and hope they are just hiding on the computer. My firefox history and add ons aren't here either. I could care less about those just saying this if it helps.

If you need any more information about what happen with ubuntu iso

[http://ubuntuforums.org/showthread.php?t=2087940&page=2](http://ubuntuforums.org/showthread.php?t=2087940&page=2)

---

### Post by oldfred on 2012-12-02
Did you fix Vista and wubi, or are you just booting off liveCD?

If you can get to wubi the Firefox profile is in your /home in .mozilla. The . means it is normally a hidden folder. Each Firefox has a profile and profile.ini says which profile to use. You probably only have the one. You can copy the profile which looks like 8 chars & .default where the 8 chars are just random. 

This is Thunderbird but it uses the same logic for profiles just it is Thunderbird in a different folder with its own profile.ini and profile.

       [http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

    
Run this from the liveCD or flash drive that you have of Ubuntu. You can download Boot-Repair into your Ubuntu and run the BootInfo report.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by carl4926 on 2012-12-02
Further to @oldfred's comments which are spot on, can I add:

In the .mozilla folder drill down as shown here
(remember the random number of your folder will be different)

.mozilla/firefox/3vbwf2j7.default/bookmarkbackups/

That's how mine looks and where you need to go
In the bookmarkbackups you will see a list of .json files
Copy them all for now, to a safe place.

Now, you can try using them. Here is how:

Make a backup of the .mozilla that you are using, then rename it to .mozilla-bak
Now start firefox, it will be completely fresh, so now you can import the most recent .json file from the ones you copied:
Ctrl+SHIFT+O
Import/Backup > Restore > Choose file

That's it, watch the magic happen.
If that file import doesn't get you back to as you would expect, you start the whole process over by deleting .mozilla and try the same process with the next file in the list... and so on

---

### Post by Gronknation on 2012-12-03
This site is awful! It only took oldfred 20 seconds to read and reply to my post. Sorry I took so long to reply guys. I'm almost Positive I'm booting from the CD but I'm going to check now and edit this post.

---

### Post by pkadeel on 2012-12-03
As you were using windows prior to this adventure :) . I guess you are still unable to recover the actual windows installation and are using the Ubuntu Live CD to dive into your lost data and recover it to a safe place. So on windows (XP, vista, 7), your firefox bookmarks and other firefox profile data is stored in the drive on which windows was installed mostly C:\
the folder structure is something like
```
C:\Documents and Settings\YourUsername\Application Data\Mozilla\Firefox
```
While booting from Live CD you will not be able to identify the drive as "C:" but you can check all hdd partitions and this folder shall be present on the root of any one of the partitions.

It will be better to copy the whole "Documents and Settings" folder because other than firefox bookmarks, it also contains various other user files which you might have stored on your desktop, documents, favourits etc

Copy it to a safe location from where you can dig further for your required files and book marks.

I hope it helps.

---

### Post by carl4926 on 2012-12-03
> This site is awful! It only took oldfred 20 seconds to read and reply to my post. 
FYI
Some advanced users have prepared replies that they can copy quickly, where it addresses a common subject/support question

---

### Post by Gronknation on 2012-12-04
When I wrote my last post I was planning to try some of the stuff you guys offered. Well, I slept 13 hours! Trying them now. I am searching .mozilla/firefox from my computer. It's taking forever though it's been 20 minutes and it's still been searching.

I can't believe I didn't say this earlier but I want to go back to Windows. No offense to anyone here but I can't stand ubuntu!

---

### Post by Gronknation on 2012-12-04
I searched

C:\Documents and Settings and
.Mozilla/Firefox

And my computer wouldn't come up with anything. 

But I guess I am smarter than my computer. I found Documents and Settings (but my computer couldn't :o)

It has folders for both user accounts I had on my windows computer (default user and John)

I went:

Documents and Settings > John > Apllication Data > Mozilla > Firefox > Profiles > qkxanhik.default > bookmarkbackups

(< means I went then to the next thing)

the files there are

bookmarks-2012-11-03.json
bookmarks-2012-11-04.json
bookmarks-2012-11-05.json
bookmarks-2012-11-07.json
bookmarks-2012-11-08.json
bookmarks-2012-11-11.json
bookmarks-2012-11-12.json
bookmarks-2012-11-13.json
bookmarks-2012-11-17.json
bookmarks-2012-11-18.json

Have two questions

1. Why don't these go in order. Did I lose some bookmarks?
(Example: There is no 11-14 11-15 11-16)

2. I had around 50-60 favorites (I was the kind of "ohh that site looks cool let me save it! I was going to go threw all of these in about a week) does that look like the right amount of files for 50-60 favorites?

I didn't even need to find the .mozilla folder:D

---

### Post by pkadeel on 2012-12-05
As I have completely shifted to linux and do not use windows any more so I can't guide you through on how to recover the firefox bookmarks from these files on windows however if you have decided to go back to windows then you will most probably do a fresh install. In that case this "Documents and Settings" folder which you recovered from your current installation will be helpful to get your current files back so keep it on a separate disk when you do a windows installation.

---

### Post by Gronknation on 2012-12-05
Yeah that's what I was planning to do. I just want to make sure I have all my favorites. I just wondered why the json files didn't go in order (no 11-01,11-02,11-06 etc.)

---

### Post by oldfred on 2012-12-05
I do not know for a fact, but guess that either you did not use computer on some days or did not add any new bookmarks so it did not see a need for a new backup.

Some info here:
[http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox](http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox)

---

### Post by Gronknation on 2012-12-07
OK thanks for the help. I'm re-setting my computer back to windows tonight. I'll let you know how it works.

---

### Post by Gronknation on 2012-12-22
Finally saved up for an external hard drive. But when I'm copying my stuff to the external hard drive I keep getting this error message.

There was an error when reading the folder "Temporary Internet Files"

I click show more details (it says...)
Too many levels of symbolic links


It also does this for "history" and "application data"




Am I losing important stuff, such as my firefox favorites?

---

### Post by carl4926 on 2012-12-22
> **Gronknation said:**
> Finally saved up for an external hard drive. But when I'm copying my stuff to the external hard drive I keep getting this error message.

There was an error when reading the folder "Temporary Internet Files"

I click show more details (it says...)
Too many levels of symbolic links


It also does this for "history" and "application data"




Am I losing important stuff, such as my firefox favorites?

Whenever I copy my .mozilla folder I first clear all the cache.
Obviously the browser needs to be closed when you actually copy the folder

---

### Post by Gronknation on 2012-12-23
I closed my browser and I still got the same messages.

How do I clear my cache?
(In order to clear my cache would I delete the firefox temporary internet files?)

---

### Post by carl4926 on 2012-12-23
Tools > Clear recent history

---

