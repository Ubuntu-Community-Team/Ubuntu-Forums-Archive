---
title: "intrepid: changed desktop rotation can't use gnome"
date: 2008-07-31
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jnw222 on 2008-07-31
i accidently changed the desktop rotation by mistake and now when i try to use gnome it goes back to the login screen

xfce and Kde work well untouched

how do i undo the change in a terminal, in xfce, or in kde

---

### Post by jnw222 on 2008-07-31
i need to use gnome again but how

---

### Post by braddcadd on 2008-07-31
First try logging into the command line only and starting gnome from there:
```

startx

```

Second try installing gnome again:
```

sudo aptitude install gnome

```

Last try un-installing and re-installing gnome:
```

sudo aptitude remove ubuntu-desktop
sudo aptitude install ubuntu-desktop

```

---

### Post by braddcadd on 2008-07-31
Do you see any errors in the xorg log?

System->Administration->System log

---

### Post by jnw222 on 2008-07-31
done 

i typed in
gnome-display-properties (found from live cd)

crooected

---

