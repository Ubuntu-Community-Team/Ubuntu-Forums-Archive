---
title: "Lock kernel verson in Synaptic?"
date: 2007-04-09
forum: Installation &amp; Upgrades
---

### Post by Mimsy on 2007-04-09
I recently decided that I had had a long enough break from my ongoing war with Ubuntu, and installed Edgy again. I went with Edgy because it seemed logical that a newer version would have a touch better hardware support, and so would be more likely to be able to get my laptop wireless again. (It hasn't been able to do that for months... which, naturally, is extremely anoying.)

Since I have seen a lot of users here on the forums have so much wireless problems with kernel 2.6.17.11 that they eventually ended up going back to 2.6.17.10, I decided to keep that version, sice that was the one I installed. How do I keep the automatic updates from constantly glowing orange up in the corner, and irritate me? I highlighted the packages in Synaptic selected Properties -> Lock Version, but the reminder is still there, after multiple reboots.

What else do I need to do to be reminded only of the updates I actually want?

Thanks,
Mimsy

---

### Post by zvacet on 2007-04-09
Did you highlighted linux image 2.6.17-10?

---

### Post by Mimsy on 2007-04-09
Yes, I did. Preferences -> Lock version...

But it is still marked for upgrade in Synaptic, and the Automatic Updates function still wants to install it. Kind of odd, since that method worked really well in Dapper.

/Mimsy

---

### Post by zvacet on 2007-04-09
I don´t make any promise but try this
```
sudo aptitude forbid-version package_name
```

---

### Post by Mimsy on 2007-04-10
I tried that command, and as far as I can tell, from the messages the terminal gave me, it seems to be working in Aptitude. The orange notification icon is still there, unfortunately, prompting me to install the four kernel packages.

Any other options I can try?

Edit:
After searching for and installing some applications in Synaptic, I noticed that the "Lock Version" thing I did there seems to be working as well. So it seems to me as if I need to find the options/preferences for the Update Notifier, and do the same thing there. I will try that next.

---

### Post by Mimsy on 2007-04-11
My seemingly brilliant plan failed miserably and completely. There seems to be no way, at least none that I could find, to change the Preferences for the automatic update manager.

So now I seem to be back to where I started. I am open to suggestions.

/Mimsy

---

