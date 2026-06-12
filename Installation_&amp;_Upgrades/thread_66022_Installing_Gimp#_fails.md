---
title: "Installing Gimp# fails"
date: 2005-09-15
forum: Installation &amp; Upgrades
---

### Post by beate on 2005-09-15
Hi,

I just wanted to install [Gimp#](http://gnomefiles.org/app.php?soft_id=571) on my hoary, but I didn't get it.

That's what I did:
[list=1]
[*]Downloaded package
[*]extracted to /opt/gimp-sharp-0.7
[*]installed gcc, cpp, g++, mono
[*] ./configure
[/list] 
fails with ..."consider adjusting the PKG_CONFIG_PATH"....

So I tried ```
apt-get build-dep tomboy
``` (I found this [here](http://ubuntuforums.org/showthread.php?t=180)).

Then ./configure runs well, but make ended in
```

.....
gimp.c:78: error: syntax error before '*' token
gimp.c: In function `gimp_main_wrapper':
gimp.c:80: error: `info' undeclared (first use in this function)
gimp.c: At top level:
gimp.c:84: error: `n_return_vals' used prior to declaration
gimp.c:85: error: syntax error before '*' token
gimp.c:85: error: `return_vals' used prior to declaration
gimp.c:85: warning: data definition has no type or storage class
make[2]: *** [gimp.lo] Error 1
make[2]: Leaving directory `/opt/gimp-sharp-0.7/wrapper'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/opt/gimp-sharp-0.7'
make: *** [all] Error 2

```

What I'm I making wrong?
Thanks, Beate

---

### Post by gogomon on 2005-09-15
> fails with ..."consider adjusting the PKG_CONFIG_PATH".... 
this happended to me before and the way I solved it was by looking for the location where the pkgconfig tool put its files. I suggest to check the /usr/local/lib/pkgconfig thats where I found mine to be at. Anyhow after so you can so PKG_CONFIG_PATH=/usr/local/lib/pkgconfig && export PKG_CONFIG_PATH

---

### Post by beate on 2005-09-16
Thanks, but it doesn't helped :(

The error with "consider adjusting the PKG_CONFIG_PATH" was away before, make still ends with that error.

---

