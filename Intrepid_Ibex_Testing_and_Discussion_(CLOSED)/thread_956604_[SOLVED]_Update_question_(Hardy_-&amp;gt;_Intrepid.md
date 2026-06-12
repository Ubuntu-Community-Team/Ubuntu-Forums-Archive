---
title: "[SOLVED] Update question (Hardy -&amp;gt; Intrepid)"
date: 2008-10-23
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Noxn on 2008-10-23
Just a dumb question:
When intrepid comes out, and i do the update, is my Ubuntu totally updated (Like if id install it from the livecd)(I know i will keep my data etc, im just asking if that will be a total update)

---

### Post by beno1990 on 2008-10-23
Only the packages which have changed in the new release will be updated, which is probably the majority of packages on your system, but all of your data (home folders, accounts, etc) will be preserved as long as the update process goes well. It's essentially changing the repo the package manager looks at and downloading the new versions from there. But if you have any packages which are the same version as in the Intrepid repo, they'll be left as-is.

---

### Post by Noxn on 2008-10-23
No, i know that my system will keep all the data.

To explain you what im asking:
After the update, should i still say that I use hardy (the version im running now) or should i say that I am using intrepid?

I want to know if the SYSTEM (not my data, I KNOW I WILL KEEP MY DATA) will be fully updated like a new installation. So that it has everything intrepid has.



If you don't understand this question then just don't post, i know my English is crap.

---

### Post by Ryadt on 2008-10-23
What you will be doing will be an upgrade not just an update.
It will upgrade your system to Intrepid completely. Your system will be Ubuntu Intrepid Ibex 8.10.

---

### Post by Nepherte on 2008-10-23
The distribution upgrade *should* go without data loss. But of courrse, nothing is perfect and sometimes the system breaks on upgrading to a newer version. It is *always* advised to backup important data before you undertake such a change.

---

### Post by prshah on 2008-10-23
> **Noxn said:**
> 
When intrepid comes out, and i do the update, is my Ubuntu totally updated (Like if id install it from the livecd)

Yes, it will be a total update, just as if you've installed fresh from a live CD, but with your custom settings and programs maintained. If you've enabled any third party repositories, (Eg, for AWN or WINE) you should disable them. If the updater finds a later version of any such software in it's repos, it will replace it.

A word of warning though; you can have custom settings for most programs in a hidden directory in your home directory. Eg, you can have compiz add-ons in ~/.compiz;  these will not be checked by the updater and hence they can cause some conflicts (it did for me; X login failed; but everything worked fine after I removed the ".compiz" directory).

---

### Post by Chris Musampa on 2008-10-23
> **Nepherte said:**
> The distribution upgrade *should* go without data loss. But of courrse, nothing is perfect and sometimes the system breaks on upgrading to a newer version. It is *always* advised to backup important data before you undertake such a change.

Word to that. Attempting to upgrade from gutsy to hardy on my 2 machines failed miserably and meant a fresh install in both cases, thankfully both had /home on a seperate partition so not too painfull.

---

### Post by Noxn on 2008-10-23
> **Ryadt said:**
> What you will be doing will be an upgrade not just an update.
It will upgrade your system to Intrepid completely. Your system will be Ubuntu Intrepid Ibex 8.10.


This is JUST what i wanted to know.

Thank you! :guitar:

PS: Gave all helpful posts a thanks. (Ryadt and prshah)

---

