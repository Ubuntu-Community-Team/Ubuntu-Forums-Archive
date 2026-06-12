---
title: "Feisty upgrade kills printer"
date: 2007-06-16
forum: Installation &amp; Upgrades
---

### Post by eugenia on 2007-06-16
I have just upgraded to Ubuntu 7.04.

I first started using Ubuntu at 5.10 and it was very good as it happily allowed me to use my CanoScan N670U scanner and my Canon BJC-255SP printer.

The Scanner stopped working (and still won't work with Ubuntu but is fine under Windows) when I upgraded to 6.10 and now the printer will not work after upgrading to 7.04.

The more I upgrade Ubuntu the more reliant I am on Windows!

I am beginning to wonder where I will be if I do any more upgrades.

Can anyone give me any suggestions as to what to look for to try to get my printer back. I have checked the driver and it's the correct one. I note that when I tried to reinstall the printer it was not detected when I ran the wizard even though it used to be detected when I was using 6.10 so the Ubuntu team must have changed something.

Is there some way to get a log file that will point to the problem area?

---

### Post by mikeescott on 2007-09-26
> **eugenia said:**
> I have just upgraded to Ubuntu 7.04.

I first started using Ubuntu at 5.10 and it was very good as it happily allowed me to use my CanoScan N670U scanner and my Canon BJC-255SP printer.

The Scanner stopped working (and still won't work with Ubuntu but is fine under Windows) when I upgraded to 6.10 and now the printer will not work after upgrading to 7.04.

The more I upgrade Ubuntu the more reliant I am on Windows!

I am beginning to wonder where I will be if I do any more upgrades.

Can anyone give me any suggestions as to what to look for to try to get my printer back. I have checked the driver and it's the correct one. I note that when I tried to reinstall the printer it was not detected when I ran the wizard even though it used to be detected when I was using 6.10 so the Ubuntu team must have changed something.

Is there some way to get a log file that will point to the problem area?






I got it working!!!!! The N670U that is

Open you package manager (System-Administration-Synaptic Package Manager)
install "libusb-dev 2:0.1.12-2"

If it does not work after that, go to [http://www.sane-project.org/](http://www.sane-project.org/) and find the "SANE-Backends-1.0.18" to download and install.

---

