---
title: "how to read out cpu temperature and fan speed am3 mb"
date: 2009-08-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by pulpo69 on 2009-08-18
how can i read out and show (in the panel) cpu temperature and fan speed.
i've an asus am3 motherboard and a phenomII X4 cpu.
Lm-sensors don't work for me.
any idea? thanks in advance.

---

### Post by miegiel on 2009-08-18
> **pulpo69 said:**
> how can i read out and show (in the panel) cpu temperature and fan speed.
i've an asus am3 motherboard and a phenomII X4 cpu.
Lm-sensors don't work for me.
any idea? thanks in advance.

```
sudo apt-get install lm-sensors
```

then to detect and add sensors to the modules file

```
sudo sensors-detect
```

then to read sensor output

```
sensors
```

what's going wrong with lm-sensors for you (sorry for not reading better)

---

### Post by Paqman on 2009-08-18
> **miegiel said:**
> 
then to read sensor output

```
sensors
```


There's also a panel applet for this: [sensors-applet]("apt:sensors-applet").

---

### Post by pulpo69 on 2009-08-18
Thanks for the advices, i will try it once more when i am at home.
i believe it the same thing i tried before. maybe the problem is that
lm-sensors can't read the sensors of my motherboard (asus am3-socket with
phenomXII cpu) and lm-sensors has no k10 support (whatever this is).

---

### Post by miegiel on 2009-08-18
> **pulpo69 said:**
> Thanks for the advices, i will try it once more when i am at home.
i believe it the same thing i tried before. maybe the problem is that
lm-sensors can't read the sensors of my motherboard (asus am3-socket with
phenomXII cpu) and lm-sensors has no k10 support (whatever this is).

That's true, lm-sensors doesn't support the sensor on the k10 CPUs, but normally lm-sensors does support the sensor output of the motherboard sensor, wich also reads the CPU temperature.
[COLOR="Silver"]On the AMD motherboards I've used any way, on my new intel laptop i get the reading from the CPU sensor but nothing else.[/COLOR]
Keep an eye on the confidence value *sensors-detect* gives for each sensor it finds, values like 3 and 4 are bad, values like 8 and 9 are good. Also on new hardware */etc/sensors.conf* or */etc/sensors3.conf* might require some tweaking.

---

### Post by pulpo69 on 2009-08-18
i tried out all, but nothing worked, with the sensors-applet i can only see
the temperature of the harddisc and saying to "no sensors found".

---

### Post by mdurham on 2009-08-30
> **pulpo69 said:**
> i tried out all, but nothing worked, with the sensors-applet i can only see
the temperature of the harddisc and saying to "no sensors found".

It's exactly the same for me, I think sensors don't work at the moment.

---

### Post by pulpo69 on 2009-08-31
you can try mbmon it shows you temperature and fans n the console.

---

### Post by mdurham on 2009-08-31
> **pulpo69 said:**
> you can try mbmon it shows you temperature and fans n the console.
Thanks. I tried mbmon but get the message "No Hardware Monitor found!!" any clues on this?

---

### Post by daponz on 2009-08-31
Regarding CPU temperature you can give a look at [http://ubuntuforums.org/showthread.php?t=1021931]("http://ubuntuforums.org/showthread.php?t=1021931")

It worked for me.

---

