---
title: "brasero and compiz are kept back for some time"
date: 2009-11-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by zika on 2009-11-27
```
The following packages have been kept back:
brasero compiz-core compiz-gnome compiz-plugins libbrasero-media0
```
For compiz apt(itude) suggests removing compiz-wrapper.
Any ideas?

---

### Post by yelo3 on 2009-11-27
for sure compiz can be upgraded without problems, but I think that for brasero we need to wait

---

### Post by zika on 2009-11-27
> **yelo3 said:**
> for sure compiz can be upgraded without problems, but I think that for brasero we need to waitLet it uninstall compiz-wrapper?

---

### Post by jppr on 2009-11-27
> **zika said:**
> Let it uninstall compiz-wrapper?

update your system in synaptic and everything goes rightway... :popcorn:

---

### Post by philinux on 2009-11-27
> **zika said:**
> Let it uninstall compiz-wrapper?

Yes.

---

### Post by zika on 2009-11-27
> **philinux said:**
> Yes.Done.

---

### Post by zika on 2009-11-27
> **jppr said:**
> update your system in synaptic and everything goes rightway... :popcorn:Synaptic is a slippery road for testing period ... in Karmic testing that was a recipe for ... let's say problems ... I use aptutude safe-upgrade ...

---

### Post by jppr on 2009-11-27
> **zika said:**
> Synaptic is a slippery road for testing period ... in Karmic testing that was a recipe for ... let's say problems ... I use aptutude safe-upgrade ...

Synaptic do update always safeway. i have use it now 2 years and i don´t need think any partial upgrade system or can i update system now,
and updates come from mainserver and i use proposed packages without any problems.

---

### Post by zika on 2009-11-27
> **jppr said:**
> Synaptic do update always safeway. i have use it now 2 years and i don´t need think any partial upgrade system or can i update system now.I choose to disagree. Just take a look at discussions we had while testing Karmic. The only way to be safe with Synaptic is to refuse any upgrade when it wants to remove something. That is just my opinion...

---

### Post by yelo3 on 2009-11-27
That's not true, you have to read package changelogs to understand if a package can be removed safely.

---

### Post by zika on 2009-11-27
> **yelo3 said:**
> That's not true, you have to read package changelogs to understand if a package can be removed safely.Changelogs were unavailable at the time I posted my question. I do check them whenever such a situation arises. I do read lucid development mailing list messages regularly... OK, I do not want to repeat the whole thread we had when testing Karmic ...

---

### Post by Amaranth on 2009-11-27
compiz-wrapper is no longer used (I wrote the important bits right into the C code) so that is fine to remove. I know you already did but I just wanted to make sure the information was out there.

---

### Post by zika on 2009-11-28
> **Amaranth said:**
> compiz-wrapper is no longer used (I wrote the important bits right into the C code) so that is fine to remove. I know you already did but I just wanted to make sure the information was out there.Thank You.

---

