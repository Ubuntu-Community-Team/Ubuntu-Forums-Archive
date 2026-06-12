---
title: "Firefox 3.6.7 upgrade this morning lost my bookmarks"
date: 2010-07-23
forum: Installation &amp; Upgrades
---

### Post by grikdog on 2010-07-23
Ubuntu upgraded my old Firefox 3.0.x to Firefox 3.6.7 this morning.  Not bad, I've been waiting for the Update Manager to get around to this for months!

However, because of a confusing startup message about "use 3.5" bookmarks (when I'm clearly using 3.0x!), my bookmarks disappeared.

Nor do they turn up in the usual .mozilla profile places (!??), so where are my old "3.5" bookmarks that are actually 3.0.x??

I can always do a hard restore from external backup, but Firefox has never screwed up my system before, so I assume it hasn't this time either.

Any ideas?

This is Dell Inspiron 1525 running Jaunty 9.04.

TIA,
d

---

### Post by RadiantPhoenix on 2010-07-23
I had the same problem. I found my lost files in ~/.mozilla/firefox.2-replaced after a bit of serious panicking.

---

### Post by grikdog on 2010-07-23
Many other problems, including Java and Vimeo...

In a nutshell, Firefox 3.6.7 did more damage in five minutes this morning than ANY hacker, cracker, blackhat or wingnut has done with malice aforethought to any computer I've ever owned since 1984.

Nice "work" kiddies.

---

### Post by grikdog on 2010-07-23
> **RadiantPhoenix said:**
> I had the same problem. I found my lost files in ~/.mozilla/firefox.2-replaced after a bit of serious panicking.

Uhhh...  The bookmarks.html file in this folder is moz-specific, no user provided content.  Can you be more specific?

What is .json file, e.g.?

---

### Post by RadiantPhoenix on 2010-07-23
Firefox can import the .json file

Go to the Bookmarks menu -> organize bookmarks, import and backup -> Restore -> Choose File... , Then navigate to the directory with your 3.0 bookmarks file and import it.

EDIT: I was also able to get my saved passwords by copying the following files from the old directory to the new one:

key3.db
signons.sqlite
signons3.txt

---

### Post by Georgesl on 2010-07-24
My 3.0-3.6 update seemed to go OK on Jaunty.  Bookmarks are in place and everything seems to work OK (Java, videos, etc).

I noticed that the descriptions provided in Update Manager talked about moving some files around.  Perhaps that didn't get done for some folks.

I'm in the habit of holding off for a day or two whenever presented with updates.  Gives the developers time to fix some of the "oh s***" issues before they get to me.

---

### Post by brotherbrian on 2010-07-25
NOt only did I lose my bookmarks,  but I also lost all ability to play video. I just get a giant "play" arrow, and when I click it, it turns black, but no video ever plays.

---

### Post by grikdog on 2010-07-25
> **brotherbrian said:**
> NOt only did I lose my bookmarks,  but I also lost all ability to play video. I just get a giant "play" arrow, and when I click it, it turns black, but no video ever plays.

This is a problem with one or more plugins.  As a first step, remove AdBlock Plus and/or NoScript.  Video (Youtube, Vimeo, weather radar animations, etc.) will also work if you configure those two plugins right.  E.g., allow ytimg.com in NoScript (I think) to get YouTube working.  I leave it to others to decide whether this is a Good Thing, considering some of the other gotchas.

3.6.7 can open EVERY TAB in a folder of urls just by hitting the wrong key.  If your Lucid Lynx screensaver goes off, then times out, you will be staring at a rack of unusable tabs with an Unlock modal window hiding behind them.  No help for it, but to press Ctl-Alt-Backspace and bail.

On the other hand, php seems to be broken.  This is the culprit that generates an endless stream of empty tabs, followed by lockup when the screensaver times out and locks.

---

