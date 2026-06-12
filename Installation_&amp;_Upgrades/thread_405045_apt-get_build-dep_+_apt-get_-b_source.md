---
title: "apt-get build-dep + apt-get -b source"
date: 2007-04-09
forum: Installation &amp; Upgrades
---

### Post by burgerbee on 2007-04-09
I want to install Ubuntu with debootstrap and then compile for PPC64 (Xbox 360). I have Ubuntu 7.04 Beta running on the 360 now but I want more optimization. 

A was thinking something like this could work after debootstrap:

```

sudo apt-get build-dep ubuntu-desktop -y
sudo apt-get -b source ubuntu-desktop -y

```

**Questions:**
1. Compiling single packages like above works fine but binarys doesnt end up in the right folders and it is very messy when working on many packages. This cant be the way to go.

2. I want dpkg-buildpackage to use architecture PPC64 or in other words something like below. Did some speedtests on the 360 with diffrent compiler options. Where can i tell dpkg-buildpackage to use " -mpowerpc64 -Os"?


```


bongy@xbox360:~$ gcc -mpowerpc speedtest.c -o speed;./speed
10E6 RDTSC time=1862 ms
10E6 RDTSC time=1863 ms
10E6 RDTSC time=1862 ms
bongy@xbox360:~$ gcc -mpowerpc64 speedtest.c -o speed;./speed
10E6 RDTSC time=1812 ms
10E6 RDTSC time=1812 ms
10E6 RDTSC time=1812 ms
bongy@xbox360:~$ gcc -mpowerpc -Os speedtest.c -o speed;./speed
10E6 RDTSC time=708 ms
10E6 RDTSC time=709 ms
10E6 RDTSC time=708 ms
bongy@xbox360:~$ gcc -mpowerpc64 -Os speedtest.c -o speed;./speed
10E6 RDTSC time=702 ms
10E6 RDTSC time=702 ms
10E6 RDTSC time=702 ms

```

3. Is there a build-your-own-optimized-ubuntu-repository-i-do-it-all-for-you script out there? :-)

/BurgerBee

---

