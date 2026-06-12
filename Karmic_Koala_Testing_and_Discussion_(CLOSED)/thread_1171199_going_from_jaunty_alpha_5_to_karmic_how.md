---
title: "going from jaunty alpha 5 to karmic how?"
date: 2009-05-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tgpraveen on 2009-05-27
so i am still on jaunty alpha 5 as i lost my net connection for a few months now i dont want to upgrade to jaunty stable want to go to karmic alpha directly how?

---

### Post by davideotape on 2009-05-27
> **tgpraveen said:**
> so i am still on jaunty alpha 5 as i lost my net connection for a few months now i dont want to upgrade to jaunty stable want to go to karmic alpha directly how?

I'd go stable and then alpha personally, but then again I skipped out jaunty completely and went straight from 8.10 --> 9.10. All depends how much you've got to download to go from alpha 5 to jaunty stable.

---

### Post by tgpraveen on 2009-05-27
its about 500 mb to go from jaunty alpha to stable and my connection has metered bandwith so i dont want to waste any 

pls tell me procedure to go from jaunty alpha to karmic

---

### Post by taavikko on 2009-05-27
> **tgpraveen said:**
> its about 500 mb to go from jaunty alpha to stable and my connection has metered bandwith so i dont want to waste any 

pls tell me procedure to go from jaunty alpha to karmic

i would download daily iso via torrent, then install.
That way wouldn't waste bandwidth excessive compared to upgrading to 9.04 and dist-upgrading to devel-release

---

### Post by davideotape on 2009-05-27
> **tgpraveen said:**
> its about 500 mb to go from jaunty alpha to stable and my connection has metered bandwith so i dont want to waste any 

pls tell me procedure to go from jaunty alpha to karmic

First of all, please be aware that development releases are not meant for stable computers that need to work all the time. Expect the worst and prepare for the worst.

Type this into your terminal:

```
sudo gedit /etc/apt/sources.list
```

Enter your password, hit enter, and a txt document should appear. Change all the "Jaunty"'s to "Karmic"'s, and then just update as usual.

---

### Post by davideotape on 2009-05-27
> **taavikko said:**
> i would download daily iso via torrent, then install.
That way wouldn't waste bandwidth excessive compared to upgrading to 9.04 and dist-upgrading to devel-release

Is there a problem with going straight there via sources.list?

---

### Post by taavikko on 2009-05-27
> **davideotape said:**
> Is there a problem with going straight there via sources.list?

There can be. So why take extra risks, when downloading daily iso is roughly equivalent and also great way to remove possible underlying issues what migh raise it's head during/after plain upgrade.

Used to have one system that was installed during edgy testing, then was dist-upgraded through releases to Intrepid. But I would recommend doing a clean install.

---

### Post by Sef on 2009-05-27
> Is there a problem with going straight there via sources.list?It is not recommended to do that.   

The OP would have to upgrade to Jaunty stable or do a clean install of Karmic Koala.  Due to consideration of the bandwith problem, I would recommend that the OP stay with a stable as the nonstables are constantly being updated.  Or someone can keep sending him updated cds.

---

### Post by davideotape on 2009-05-27
> **Sef said:**
> It is not recommended to do that.

Purely out of interest, why not? I uses the sources.list method to go straight from intrepid to karmic, so am I at a greater risk of breakages, or will my bugreports be invalid?

As for the bandwidth issue, I would also not recommend using development releases if you have limited d/l limits. At it's peak there is over 100MB a day in updates.

---

### Post by psyke83 on 2009-05-27
> **davideotape said:**
> Purely out of interest, why not? I uses the sources.list method to go straight from intrepid to karmic, so am I at a greater risk of breakages, or will my bugreports be invalid?

You're asking a question that has a difficult answer. Many packages have specific assumptions about what's installed on your system and may not behave properly if your system doesn't match. There may have been a workaround or change introduced in the Intrepid -> Jaunty package transition that wasn't accounted for in Karmic's packages.

You're at a greater risk of breakages, but I'll leave the exact details to someone who knows about it better than I.

---

