---
title: "Lucid-Feb 11 status: Has the &quot;Enter key&quot; X &amp; Plymouth issue resolved yet?"
date: 2010-02-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by emarkay on 2010-02-11
Just want to know if I can update and not have all that happen again.
Thanks

---

### Post by VMC on 2010-02-11
**No!**

I thought Plymouth problem was resolved but after three reboots the problems is back, exactly as before. Removing Plymouth fixed my freeze.

I was excited at first. I rebooted twice then thought maybe shutdown and boot up again would be the telling tale. Sadly it was.

My question is, if its not directly a Plymouth problem, removing Plymouth fixes my freeze. What else could it be. The messages stop and then somethings going on but no output message flow, then the screen light extinguishes, and computer freezes.

---

### Post by Stik on 2010-02-11
If you are talking about the freeze after hitting enter key after boot I still have it after latest updates... Logging out and back in stops the freezing until next boot..

---

### Post by LKjell on 2010-02-12
I have to kill X. Sometimes I have to kill everything. Sometimes I do not have to do anything. So kinda annoying...

---

### Post by goldsniper on 2010-02-12
On my machine, I think the "ENTER key" problem has been resolved because I haven't encounter the problem for last 2 days! And for the Plymouth, still no change!

My workaround, I need to get to Grub list and then edit it.. remove quest splash seems to let me boot nicely.

---

### Post by kahumba on 2010-02-12
February 12 daily build, the issue is (still) there.

---

### Post by MacUntu on 2010-02-12
For many it has, but not for all. See [https://bugs.launchpad.net/bugs/516412]("https://bugs.launchpad.net/bugs/516412").

---

### Post by philinux on 2010-02-12
When it freeze just use Aly+SysRq+k until it's fixed.

---

### Post by tad1073 on 2010-02-12
It seems to be fixed for me, for now.

---

### Post by emarkay on 2010-02-12
OK, then for today I am calling it "don't update yet, it's working OK for now".

After removing Plymouth and doing the "edit /usr/sbin/update-initramfs and add a "exit 0" directly after set -e" fix, that was an annoying loop-de-loop to fix...

Maybe this weekend things will get resolved.   Yea it's alpha, so I expected things like this, but still...   :)

---

### Post by Kenny_Strawn on 2010-02-12
> **emarkay said:**
> OK, then for today I am calling it "don't update yet, it's working OK for now".

After removing Plymouth and doing the "**[color="Red"]gedit[/color]** /usr/sbin/update-initramfs and add a "exit 0" directly after set -e" fix, that was an annoying loop-de-loop to fix...

Maybe this weekend things will get resolved.   Yea it's alpha, so I expected things like this, but still...   :)

Your spelling error is in boldfaced text and in red.

---

### Post by emarkay on 2010-02-12
> **Kenny_Strawn said:**
> Your spelling error is in boldfaced text and in red.

Thanks, but not technically a spelling error, it's an "improper command usage" - and anyway, it's a quote lifted from another post and** anyway**, it's got to be "gksudo gedit"...  :)

---

### Post by robertbub on 2010-02-20
FWIW, this is no longer generally a problem, but seems to instead manifest itself as logging me out randomly when hitting the Enter key.

When I did a "aptitude safe-upgrade" this morning, plymouth was reinstalled and that's when I started getting logged out occasionally.  I've since removed plymouth (and therefore cryptsetup) and, so far, no unexpected logouts...

---

### Post by metallica1788 on 2010-02-21
The new kernel update today fixed it for me:)
so i think it is resolved then.:D

---

### Post by autocrosser on 2010-02-21
Hmmmm---I'll reinstall plymouth and give it a try.....

---

### Post by sparker256 on 2010-02-21
> **autocrosser said:**
> Hmmmm---I'll reinstall plymouth and give it a try.....

I reinstalled plymouth a couple days ago. I waited untill my daily live flash drive could boot and then I could go into terminal and press enter without locking up.

Bill

---

### Post by autocrosser on 2010-02-21
I wish it was fixed in my case--re-installed Plymouth & the first <enter> I hit locked the system up tight...un-installed Plymouth again-----<sigh>   i7-940 system with nvidia graphics---O'well was a nice thought......

---

### Post by emarkay on 2010-02-21
So I guess regardless Plymouth is unnecessary - I have had it removed for a week and don't have a clue what it was for anyway; at least as a productivity enhancement feature.  ;)

---

### Post by autocrosser on 2010-02-21
Just for the pretty pre-login boot up--about 30 sec or less of eye-candy before GDM. I guessed that anyone with a nvidia chipset would loose out until a workaround comes up...but I don't like that it b0rks my system whilst it looks for a clue.......

I just hate the black 30sec look.......wish the fallback was the old boot--I liked it......

---

