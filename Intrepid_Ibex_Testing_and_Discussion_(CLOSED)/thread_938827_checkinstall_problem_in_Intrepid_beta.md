---
title: "checkinstall problem in Intrepid beta"
date: 2008-10-05
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by sojyujai on 2008-10-05
I installed the latest Intrepid beta by first installing a fresh version of Hardy then upgrading to Intrepid (I couldn't manage to get a direct Intrepid install to work as my video card isn't supported by the LiveCD)

Now I'm trying to compile the latest version of x264 according to _[this howto]("http://ubuntuforums.org/showthread.php?t=786095")_

When I get to the checkinstall part it fails with the following message:
```
Installing with make install...

========================= Installation results ===========================
install -d /usr/local/bin /usr/local/include
install -d /usr/local/lib /usr/local/lib/pkgconfig
install: cannot change permissions of `/usr/local/lib/pkgconfig': No such file or directory
make: *** [install] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

```

So, I'm not sure if this is a bug in Intrepid, if it was caused by my Hardy>Intrepid upgrade, if I'm missing a package/dependency or if I'm just doing something dumb.

I searched for a pkgconfig directory and found two at:
/usr/lib/pkgconfig
and 
/usr/share/pkgconfig
but none at
/usr/local/lib/pkgconfig

so could it be that an environment variable is incorrectly set to the /usr/local/lib/pkgconfig directory?  Or is something else missing here?

---

### Post by bodhi.zazen on 2008-10-05
Hard to say.

You could try :

```
sudo mkdir /usr/local/lib/pkgconfig
```

Also, you should probably choose a better title. It is not clear you issue is with either Intrepid or Checkinstall, but rather x264

---

### Post by plun on 2008-10-05
It compiles ok for me and one dependency is changed for Intrepid.

liblame-dev > libmp3lame-dev

About:
[http://packages.ubuntu.com/intrepid/libmp3lame-dev](http://packages.ubuntu.com/intrepid/libmp3lame-dev)


EDIT

Brakes during ffmpeg

```
install -d "/usr/local/lib"
install -m 644 libavutil/libavutil.a "/usr/local/lib"
ranlib "/usr/local/lib/libavutil.a"
install -d "/usr/local/include/libpostproc"
install: cannot change permissions of `/usr/local/include/libpostproc': No such file or directory
make: *** [install-headers] Error 1

****  Installation failed. Aborting package creation.
```


libpostproc...

---

### Post by sojyujai on 2008-10-05
> **bodhi.zazen said:**
> 
You could try :

```
sudo mkdir /usr/local/lib/pkgconfig
```

Well, I'll be darned - that seemed to do it.  Such a simple thing I probably should have tried it before posting.

> **bodhi.zazen said:**
> 
Also, you should probably choose a better title. It is not clear you issue is with either Intrepid or Checkinstall, but rather x264
You maybe right, at the time I posted I thought this was a general problem with checkinstall on intrepid.  I'm still not really clear where the blame lies - is x264 trying to use an invalid directory in Intrepid or is Intrepid missing the required directory?  Or should x264 look for the directory and if it doesn't find it, then it should create it instead of failing.  Beyond me...

---

### Post by sojyujai on 2008-10-05
> **plun said:**
> It compiles ok for me and one dependency is changed for Intrepid.

liblame-dev > libmp3lame-dev

About:
[http://packages.ubuntu.com/intrepid/libmp3lame-dev](http://packages.ubuntu.com/intrepid/libmp3lame-dev)


EDIT

Brakes during ffmpeg

```
install -d "/usr/local/lib"
install -m 644 libavutil/libavutil.a "/usr/local/lib"
ranlib "/usr/local/lib/libavutil.a"
install -d "/usr/local/include/libpostproc"
install: cannot change permissions of `/usr/local/include/libpostproc': No such file or directory
make: *** [install-headers] Error 1

****  Installation failed. Aborting package creation.
```


libpostproc...

Thanks for the info about the new dependency.  Does that apply to just ffmpeg or to x264 as well?  I just built x264 before reading your post and I have liblame-dev installed.  Hope that's not an issue.  I'll change the liblame-dev to libmp3lame-dev before building ffmpeg.
Edit - oops, no I didn't have liblame-dev installed after all. 

I guess your libpostproc might be the same problem I had with pkgconfig.  A sudo mkdir might fix it.  I'll let you know if I had a similar problem.

---

