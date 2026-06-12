---
title: "LTS server with GUI as a Desktop?"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by Penguinnerd on 2011-10-14
I'm wondering about this on a purely hypothetical basis, mainly because I'm curious about how Ubuntu Server relates to the Desktop release.

Please correct me where/if I'm wrong:

LTS is supported for three years. Server LTS is supported for five years.

The main functional difference between Desktop and Sever releases seems to be the lack of a GUI in the default server install, but it is possible to install a fully functional GUI in the server version as well.

And now the question:
Is there any reason why someone couldn't install the LTS server version, and configure it for desktop use? This would allow the user to receive a full five years of support/updates on a particular version of the OS.

---

### Post by Dangertux on 2011-10-14
> **Penguinnerd said:**
> I'm wondering about this on a purely hypothetical basis, mainly because I'm curious about how Ubuntu Server relates to the Desktop release.

Please correct me where/if I'm wrong:

LTS is supported for three years. Server LTS is supported for five years.

The main functional difference between Desktop and Sever releases seems to be the lack of a GUI in the default server install, but it is possible to install a fully functional GUI in the server version as well.

And now the question:
Is there any reason why someone couldn't install the LTS server version, and configure it for desktop use? This would allow the user to receive a full five years of support/updates on a particular version of the OS.

You would receive security updates to the operating system itself. However any desktop applications you used, as well as the desktop environment and X server itself wouldn't be updated in repos after end of life. 

However you could easily install the packages from source and get updates for as long as they were being developed if you were so inclined. So in theory it's not a bad idea, just more complicated than most people are actually willing to do.

---

### Post by Penguinnerd on 2011-10-14
Ah, thanks. I figured it was something like that.

---

