---
title: "Google Earth 5 will not show embedded pictures"
date: 2009-04-21
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Technoviking on 2009-04-21
When I click on the little blue squares in the satellite view, only a big white placeholder window for the picture is shown, but no picture is embedded. Only a small question mark is shown in the middle of a the rather large white window, clicking on it brings me to Firefox.

Is Anyone else seeing this problem?

T-V

---

### Post by alphacrucis2 on 2009-04-22
> **Technoviking said:**
> When I click on the little blue squares in the satellite view, only a big white placeholder window for the picture is shown, but no picture is embedded. Only a small question mark is shown in the middle of a the rather large white window, clicking on it brings me to Firefox.

Is Anyone else seeing this problem?

T-V

Just tried it. I get the same result.

---

### Post by plun on 2009-04-22
OK with nVidia graphic and GE ver 5.0.11337.1968 (beta)

[[img]http://ubuntu-pics.de/thumb/12819/snapshot34_E4kx9n.png[/img]](http://ubuntu-pics.de/bild/12819/snapshot34_E4kx9n.png)

---

### Post by alphacrucis2 on 2009-04-22
> **plun said:**
> OK with nVidia graphic and GE ver 5.0.11337.1968 (beta)

[[img]http://ubuntu-pics.de/thumb/12819/snapshot34_E4kx9n.png[/img]](http://ubuntu-pics.de/bild/12819/snapshot34_E4kx9n.png)

My version is the same Google Earth 5.0.11337.1968 (beta). ATI fglrx graphic driver with HD3400. My screen shot attached.

---

### Post by plun on 2009-04-22
OpenGL info

```
plun@plun:~/glxdragon$ ./glxdragon
GL_VENDOR   : NVIDIA Corporation
GL_RENDERER : GeForce 8600 GT/PCI/SSE2
**GL_VERSION  : _3.0.0_ NVIDIA 180.51**

```


It might be a opengl challenge ?

---

### Post by Reiger on 2009-04-22
Huh... I don't even get Google earth 5 at all (installed under /opt), once it tries to connect:
```

./googleearth-bin: relocation error: /lib/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 notdefined in file libcrypto.so.0.9.8 with link time reference
```

---

### Post by plun on 2009-04-22
> **Reiger said:**
> Huh... I don't even get Google earth 5 at all (installed under /opt), once it tries to connect:
```

./googleearth-bin: relocation error: /lib/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 notdefined in file libcrypto.so.0.9.8 with link time reference
```

This bug is fixed in the Medibuntu version.

[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

--

---

### Post by alphacrucis2 on 2009-04-22
> **plun said:**
> This bug is fixed in the Medibuntu version.

[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

--

Ah that's why I didn't have that bug:lolflag:. Anyhow, here is my output from glxdragon. (I didn't have that installed already).

```

GL_VENDOR   : ATI Technologies Inc.
GL_RENDERER : ATI Mobility Radeon HD 3400 Series
GL_VERSION  : 2.1.8575

```

---

### Post by cl333r on 2009-04-22
I got 64 bit Jaunty and Google Earth 5 crashes with:
```

./googleearth-bin: relocation error: /lib32/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference

```

---

### Post by Technoviking on 2009-04-22
Uninstalling medibuntu package and making deb from googleeath-package worked. Fonts not as smooth.

T-V

---

### Post by kabloink on 2009-04-22
> **Technoviking said:**
> Uninstalling medibuntu package and making deb from googleeath-package worked. Fonts not as smooth.

T-V

That fixed the problem with the embedded pictures for me also. 

Has anyone gotten the youtube videos to work in Google Earth?

---

### Post by Lunx on 2009-04-22
> **Technoviking said:**
> When I click on the little blue squares in the satellite view, only a big white placeholder window for the picture is shown, but no picture is embedded. Only a small question mark is shown in the middle of a the rather large white window, clicking on it brings me to Firefox.

Is Anyone else seeing this problem?

T-V


LOL, I only installed GE into Jaunty a few hours ago and noticed exactly this behaviour myself. Glad to know it isn't only me then, hopefully there may be a fix to come. Also I can't get GE to open Firefox, and can't see any preference settings in GE where I can try to point it at my browser.

---

