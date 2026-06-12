---
title: "HowTo: Enable Surround Sound"
date: 2009-01-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ace214 on 2009-01-18
I'm not sure if this is the case for everyone but my surround sound did not work initially when I install Jaunty. I think there used to be a properties window under preferences where one could enable surround sound for different types of sound (music/movies/sound events).

This is what I had to do to get my surround sound working. I thought I would post it since there's no apparent GUI way of doing this.

```
sudo gedit /etc/pulse/daemon.conf
```

Scroll down to the bottom of the document (line 73 for me) and change 
```
;  default-sample-channels = 2
```

to

```
default-sample-channels = X
```

Whereas X is the number of channels you want, for example 6 for a 5.1 surround system, 8 for a 7.1, 3 for a 2.1, etc. Deleting the semicolon uncomments the line so that it is actually processed.

Hope this is helpful.

---

### Post by rudenko_ruslan on 2009-01-19
> ; default-sample-format = s16le
; default-sample-rate = 44100
default-sample-channels = 6
Is it OK?

---

### Post by durand on 2009-01-19
> **rudenko_ruslan said:**
> Is it OK?

Yup.

---

### Post by halovivek on 2009-01-19
i am using alsa base.
how to configure ?
i have solved the sound issue from this [thread]("http://ubuntuforums.org/showthread.php?t=1005416"). but i want to make it the surround sound.

---

