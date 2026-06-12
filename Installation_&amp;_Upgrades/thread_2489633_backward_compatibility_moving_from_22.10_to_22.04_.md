---
title: "backward compatibility moving from 22.10 to 22.04 ok?"
date: 2023-08-05
forum: Installation &amp; Upgrades
---

### Post by F W Adams on 2023-08-05
I moved onto 22.10 with gnome, not sure why as I usually stay with LTS.

Now the support for 22.10 has stopped. Am happy to do a new install. Is it safe just to backup data, install 22.04 on a new system then reload data. Will there be any compatibility problems?

Any help / warnings appreciated.

F W Adams

---

### Post by Tadaen_Sylvermane on 2023-08-05
Shouldn't be a problem save a few things. I know when I've migrated between Debian and Ubuntu my Evolution and Firefox settings didn't cross over. I'm guessing one was a newer version than the other and it changed something that the old one couldn't understand when I flipped back. Otherwise I haven't  had an issue. Flatpaks mitigate these issues.

Why don't you just upgrade to 23.04?

---

### Post by TheFu on 2023-08-05
Nope.  Going backwards risks config file and config DB changes that are incompatible.  Programmers don't make software that can be rolled back 99% of the time.

They expect people who want to do that to have "backups".  So, if you have a backup of your 22.04 system, restore that, then you can probably restore updated documents, but I wouldn't attempt to restore upgraded DBMS files and dconf/gconf files are likely incompatible, so changes to settings, made since the 22.04 backup was created will need to be lost.

All of this depends on what you mean by "data".

I'd say there will be compatibility problems, but you'd have to find them by having corrupted files, or files that cannot be read.  Which ones depends on all the programs you use, which is different from what anyone else does.

The better upgrade plan would be from 22.10 --> 23.04 --> 23.10 in the fall and 24.04 LTS next spring/June.  Then don't upgrade off 24.04 until 26.04 (June-ish).  Please wait a few months for the early problems with every LTS to be corrected or worked around.  If you are really worried about stability, next time you are doing LTS ---> LTS ---> LTS upgrades, wait until the xx.yy.1 release happens. Skip the initial release completely.  I don't think that's possible if you have a non-LTS loaded due to the shortened support periods.  23.10 support ends in June/July, and the 24.04.1 release doesn't usually happen in that window.

Live and learn.  Don't make the mistake next time.  BTW, if you don't use Gnome as your DE, then the LTS support period for a desktop is probably 3 yrs, so it is just long enough for 24.04.1 --> 26.04.1 migrations.

Now, I do migrations shifted by 2 yrs. In early 2023, I moved off 18.04 to 20.04.x. In 2025, I'll move to 22.04.x.  I'm always trailing to have the most stable system possible.  I did my bleeding edge time with Linux releases in the 1990s.  These days my goals are simple.  Stability and data safety.  Those two concerns vastly outweigh being on "new" software. We are all different.

---

### Post by guiverc on 2023-08-05
Generally no, but it'll depend on what applications you use.

When going forward; the *developers* code the newer versions to deal with data saved by older versions of the applications, however the reverse isn't true. 

 I've reverted releases a couple of times, and had losses of data twice & thus very much avoid doing it; both times with GNOME applications (Specifically evolution or the *mail user agent* program, & Liferea or RSS feed reader), but it could occur on any application that has changed.

You can explore the application release notes for each application where your data matters to you, and assess what changes they made, and make an *educated *guess as to what problems you might encounter; in my case a database change would have made the liferea change very obvious if I'd looked before hand, though I'd have still missed the evolution change as it was more subtle.

An example of the evolution MUA problem I experienced is

I'd used a newer feature whilst using the newer release (*method to scan incoming mail & tag it a color from memory*); I thought the feature was 'neat'  as it scanned  messages as they entered my inbox & could show them (*according to rules I created*) with a color that allowed me to easily recognize different types of mail.

When I reverted to the older version of evolution; the older program didn't know how to deal with that *code* written by the newer version; thus IGNORED any mail item with a *code*. Any item that wasn't caught by a rule I'd created in the newer version  still appeared in my [older version] inbox.

It took awhile for me to notice the problem (*only a portion of my mail was showing in the app*), so until I upgraded the system to a newer release (ie. used a newer version of the GNOME evolution mail app) the evolution mail app would not show all my mail. 

Whilst using the older version (ie. *until I upgraded again to a later release*) I had to view my mail lists from terminal, as the mail was all still on disk; the older app just couldn't cope with the *code* that was added by the newer version of the app; and this was a *pain*.

In contrast the Liferea issue was easy to spot..  The older release just would **not** use the data file from the newer release; loss of all data I had there.  I had to use the newer version of the app to read it.

Why not upgrade to 23.04??    [https://help.ubuntu.com/community/LunarUpgrades](https://help.ubuntu.com/community/LunarUpgrades)

---

### Post by F W Adams on 2023-08-06
Thanks for help.

I won't try for 22.04 but go for 23.04. Then at a later stage move back to LTS. Even after that it seems better not to migrate on from there to the next LTS until forced.

---

