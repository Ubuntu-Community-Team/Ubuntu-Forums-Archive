---
title: "Fglrx 8.6 graphic corruption"
date: 2009-03-20
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by grigio on 2009-03-20
I get graphic corruption on Radeon 4850. What about you?

[https://bugs.launchpad.net/ubuntu/+bug/345511](https://bugs.launchpad.net/ubuntu/+bug/345511)

---

### Post by rbmorse on 2009-03-20
I have a Radeon HD4850 and I'm running JauntyA6.  FGLRX is fine here. 

After installing the FGLRX packages did you run the ATI configuration routine?

```
sudo aticonfig --initial -f
```

---

### Post by helliewm on 2009-03-20
I followed the workround in the lauchpad (in the first post) reinstalled fglrx and ran sudo aticonfig --initial -f. Now my 4850 is fine and compiz works.

Helen

---

### Post by grigio on 2009-03-20
> **rbmorse said:**
> I have a Radeon HD4850 and I'm running JauntyA6.  FGLRX is fine here. 

After installing the FGLRX packages did you run the ATI configuration routine?

```
sudo aticonfig --initial -f
```

Thanks I solved it

---

### Post by Bert Mariën on 2009-03-21
Also see here

[http://www.phoronix.com/vr.php?view=13559](http://www.phoronix.com/vr.php?view=13559)

---

### Post by rbmorse on 2009-03-21
The OP has an HD4850 (RV770 chipset). The FGLRX 8.6 driver is appropriate for his card.

---

### Post by grigio on 2009-04-20
OMG! this bug is still present in rc!

---

