---
title: "Affects on Thundrebird/Firefox in Upgrading from 8.10 to 9.04"
date: 2010-05-26
forum: Installation &amp; Upgrades
---

### Post by GSam on 2010-05-26
Several days ago I posted a query about the effects of upgrading from 8.10 to 9.04 in regards to Thunderbird/Firefox emails and settings. I wondered if I would lose all of my emails, addresses, bookmarks if I make this upgrade. So far there have been no responses. Maybe it is such a dumb question that no one cares to take the time to respond. I understand that I can save addresses as ldif files and I can save bookmarks and re-import them, and I can save my profile (which should contain all of my old emails), but I've never gotten the profile thing to work properly. These alternatives do not answer my question. Can someone help???

---

### Post by WinRiddance on 2010-05-26
I'm sure that there's several ways to do this but what I've done in the past was this ....
First I'd back up all of my important data. This also includes an entire backup copy of the entire home/user folder while using full admin privileges. I'd also export my FF settings & bookmarks, whatever was exportable.

After upgrading to the newer version of Ubuntu I'd install Firefox and Thunderbird. Thunderbird I'd open up, but then I'd close it again right away without actually using it. Then I'd go into the new home/user area and rename the two mozilla folders to what they already were, plus [COLOR=DarkRed]**_orig**[/COLOR] behind the existing name. Finally I'd _copy the two old mozilla folders_ from the backup over to the new home/user location.

Firefox would allow me to import everything but my passwords since I never keep them on FF for security reasons and Thunderbird would instantly recognize my old email accounts, mail folders, and even extensions the instant that I opened it up. This worked for me on upgrades to Ubuntu 9.04, 9.10, and just a couple of days ago on 10.04 Lucid. **Lucid has the new Thunderbird though** which just imported everything automatically once I told it where to look.

---

### Post by oldfred on 2010-05-26
I have had my Firefox and Thunderbird profiles in a NTFS shared partition since about 6.10 and upgraded thru 9.10. I set this up so I could convert significant other. She saw no real difference then between windows XP and Ubuntu and now Quicken & TurboTax are the only remaining windows apps. And I am about to use KMyMoney as some of a Quicken replacement.

I regularly copy the entire profiles to my portable when we travel and copy them back when we return. The portable was XP but now it also is Ubuntu. I have essentially the same file structure on both so it is easy to use NFS and rsync the computers.

I have not yet converted tbird to ver3 with 10.04 yet so I am not sure about that.

---

