---
title: "[SOLVED] path should be /usr/bin not /usr/local/bin"
date: 2008-11-27
forum: Installation &amp; Upgrades
---

### Post by nolanpro on 2008-11-27
Hi, i'm pretty new to linux and I cant figure this out. After following the ffmpeg install instructions here: [http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

it put ffmpeg into /usr/bin but when I type ffmpeg, it says ```
/usr/local/bin/ffmpeg: No such file or directory
```

If i run ffmpeg directly from /usr/bin by typing /usr/bin/ffmpeg it works but I would like to be able to run ffmpeg from other directories without having to type /usr/bin/ffmpeg, just ffmpeg.

Where do I fix these default "Paths" so it looks for it in /usr/bin instead of /usr/local/bin

Thanks for your help!

---

### Post by sisco311 on 2008-11-27
please post the output of:
```
echo $PATH
```
```
ls -al /usr/bin/ffmpeg
```
and
```
ls -al /usr/local/bin/ffmpeg
```

---

### Post by nolanpro on 2008-11-27
echo $PATH:
```
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

ls -al /usr/bin/ffmpeg
```
-rwxr-xr-x 1 root root 5442964 2008-11-27 12:55 /usr/bin/ffmpeg
```

ls -al /usr/local/bin/ffmpeg
```
ls: cannot access /usr/local/bin/ffmpeg: No such file or directory
```

Thanks for helping me with this

---

### Post by nolanpro on 2008-11-29
Works now, just had to restart the machine. Some times the simplest solutions.......

---

