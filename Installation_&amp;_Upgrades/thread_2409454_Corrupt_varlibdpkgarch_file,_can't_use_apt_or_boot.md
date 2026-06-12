---
title: "Corrupt /var/lib/dpkg/arch file, can't use apt or boot"
date: 2019-01-02
forum: Installation &amp; Upgrades
---

### Post by jthistl3 on 2019-01-02
Ubuntu 18.04 LTS, 64-bit.

I booted into Ubuntu just now, and suddenly, for seemingly no reason, it hung on the Plymouth boot screen, on 'Hold until boot process finishes up'. The boot process never finished up.

So, I looked around for solutions, and, after booting into root bash in recovery mode, I tried one. The solution involved reinstalling/removing `plymouth`, so I tried using apt to do that. But I got a locale error, which I fixed by regenerating locale.

Then, when using apt to attempt to remove plymouth, I got this error:

    ```
dpkg: error: fgets gave an empty string from 'var/lib/dpkg/arch'
```

Turns out dpkg is a bit broken.

Looking through `/var/lib/dpkg/`, most files seem intact and uncorrupted.
`available`, `diversions`, `statoverride` and `status` are all readable, largish files. The `arch` file however, is corrupt (only 11 bytes, and `cat` produces `MmSt`.)

My question is, how can I regenerate this `arch` file and fix my computer?

Even it involves reinstalling dpkg...

I'm extremely grateful for _any_ help (please)!

---

### Post by deadflowr on 2019-01-02
The arch file is only 11 bytes or so anyway.
It should read with at least one arch, usually amd64, if more then those would be listed one line each.
So you can try replacing the text with just one line that reads amd64.

If you see the splash boot screen then plymouth is more likely not the issue here.
You might try editing the boot options in the boot menu and let it run with boot log text.
Here's a helpful link to do that:
[https://wiki.ubuntu.com/DebuggingKernelBoot]("https://wiki.ubuntu.com/DebuggingKernelBoot")

---

### Post by jthistl3 on 2019-01-02
Great! Replacing it with amd64 gets rid of the error in the OP.

Now the error is:

```
dpkg: error: too-long line or missing newline in '/var/lib/dpkg/triggers/File'
```

---

