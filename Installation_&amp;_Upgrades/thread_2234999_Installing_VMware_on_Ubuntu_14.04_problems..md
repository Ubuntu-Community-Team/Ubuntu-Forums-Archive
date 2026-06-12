---
title: "Installing VMware on Ubuntu 14.04 problems."
date: 2014-07-18
forum: Installation &amp; Upgrades
---

### Post by marcus20 on 2014-07-18
Hi

Im am currently trying to install VMware Workstation 10 or 9 on ubuntu 14.04. Workstation 10 installed with a gui from terminal. 9 installed right from the terminal. Its 9 I have installed right now.

I can install both of them it seems wit little problems. However when i try to start the program i get error.

It says:

"VMware Kernal Module Updater

Befor you can run vmware, serveral modules must be compiled and loded inte the running kernel

Kernel Headers 3.13.0-32-generic
kernal headers for version 3.13.0-32-generic were not found. If you installed them in a nin defail tath you can specify the path below. Otherwise refer to your distribution's documentation for installation instructions and click Refresh to search again in the default locations.

location <text feild> <browse button> <refresh button>
<cancel button> <install button>"

If i select brows there are folders for
linux-headers-3.13.0.24
linux-headers-3.13.0.24-generic
linux-headers-3.13.0.32
linux-headers-3.13.0.32-generic

If i select linux-headers-3.13.0.32-generic and try to install it i get en error popup. "C header files matching your running kernel were not found. Refer to..."

I have run apt-get update, apt-get upgrade. I have looked around the internet for the C headers for the kernal headers that are missing but have not found much. 

uname -r: 3.13.0-32-generic
uname -v: #57-Ubuntu SMP
uname -i: x86_64

I hope this is enough information for you to be able to help me. If not, ask for what you need.

Thanks

Thanks

---

### Post by andrew143 on 2014-08-08
Marcus20,

I just had the same issue. I resolved it by sudo apt-get install linux-headers-3.13.0-32*
Then start Workstation.

I am not sure when headers it wanted but I grabbed all of them

---

### Post by ubfan1 on 2014-08-08
The package names have a hyphen before the final number, not a period.
linux-headers-3.13.0-32-generic
linux-headers-3.13.0-32

---

### Post by mobilecoreteam on 2014-09-06
i seem to recall that this parameter "linux-headers-`uname -r`' should be as generic as could be :)

---

