---
title: "OEM install asking for nameservers after oem-config-prepare"
date: 2016-02-19
forum: Installation &amp; Upgrades
---

### Post by dleemaas on 2016-02-19
[COLOR=#111111][FONT=Ubuntu]I'm trying to create an install image of server 15.10 that I can deploy to a few dozen machines by running through the OEM install, customizing packages and settings, then running "oem-config-prepare".
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]After running oem-config-prepare and rebooting (leaving out capturing the image for deployment elsewhere), while running through the install steps again, it asks me to manually input the name server addresses. If I leave it blank, resolv.conf does not auto populate from DHCP - even though DHCP is still assigning the rest of eth0's IP settings.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]In the OEM install everything was set for DHCP and DNS auto populated, and that's what I want to carry over into the deployment image. I'll provide whatever further info might be needed, but does anyone have an idea as to what's going on to cause DHCP to work but resolv.conf to not populate once I run the install again after OEM prep?
[/FONT][/COLOR]

---

### Post by SeijiSensei on 2016-02-19
You do realize that 15.10 is not a release with long-term support, right?  All those deployments will reach [end-of-life]("http://www.ubuntu.com/info/release-end-of-life") next summer.  If you are intending to deploy servers with any reasonable life span, you should be using 14.04 or waiting until 16.04 is released in April.

---

### Post by dleemaas on 2016-02-19
> **SeijiSensei said:**
> You do realize that 15.10 is not a release with long-term support, right?

I do.  Not to derail the original subject of DNS not populating, but the OEM installation feature in 14.04 is seemingly broken.

I'm not the only one with the problem, either:
[http://askubuntu.com/questions/736484/oem-install-ubuntu-server-14-04/736494](http://askubuntu.com/questions/736484/oem-install-ubuntu-server-14-04/736494)

So if you believe that the solution to this particular issue is to try to OEM install 14.04 instead, I'd be happy to take any suggestions on how to get it working.

---

### Post by SeijiSensei on 2016-02-19
Nope, I can't help with that.  I only posted because during my time here I've seen many people choose a non-LTS version because it's the one advertised on the Ubuntu home page.  That's true even for the server edition.  

Does the bug persist in the current [16.04 builds]("http://cdimage.ubuntu.com/ubuntu-server/daily/20160219/")?  If not, I'd probably use that rather than 15.10.  Most mainstream server applications have been around for years, so they're not likely to be all that unstable.

Of course, you could also try another platform like CentOS 7.

If you have to hardcode DNS addresses, you could use Google's 8.8.8.8 and 8.8.4.4.  Usually Ubuntu uses dnsmasq and resolvconf, so the default DNS server is 127.0.1.1 which dnsmasq listens on.  You might try building an image with 127.0.1.1 as the server address and see how that goes.

---

### Post by dleemaas on 2016-02-19
> **SeijiSensei said:**
> Does the bug persist in the current [16.04 builds]("http://cdimage.ubuntu.com/ubuntu-server/daily/20160219/")? ... Of course, you could also try another platform like CentOS 7.

Downloading 16.04 server now, as well as 14.04.04, since I was using 14.04.03.  I'll try the whole process out with both of them to see what results I get for both my DNS issue and the OEM install in general.  If all else fails, yes, I may try setting up my custom build in CentOS 7 instead.

> **SeijiSensei said:**
> If you have to hardcode DNS addresses, you could use Google's 8.8.8.8 and 8.8.4.4.  Usually Ubuntu uses dnsmasq and resolvconf, so the default DNS server is 127.0.1.1 which dnsmasq listens on.  You might try building an image with 127.0.1.1 as the server address and see how that goes.

Unfortunately, in our environment the only DNS server allowed is the internal one (which in turn *does* use google DNS), so for testing that's a no-go.  Where I'm deploying these machines to will be allowed to use google DNS, however.  I was just hoping that the dynamic settings would carry over, same as with a fresh install.

---

### Post by dleemaas on 2016-02-22
Well, it turns out I managed to solve both of my issues.

First, as said, the OEM installation menu option in server 14.04 does not work. It just does nothing when you select it. However, if you add "oem-config/enable=true" to the boot options manually, it works.  That at least tackled the problem of using a non-LTS build.

I wasn't running into the same DNS issue with the regular desktop install, so I took a look at what I really needed the install to do, and decided to start from the minimal install instead of server.  Go figure, everything worked using the 14.04 minimal .iso and the OEM install manual boot option.  So ultimately, there's something going on in the server install that's interfering with DNS after the "oem-config-prepare" command has been run.  Likely a dnsmasq issue, as you pointed out.

Either way, I managed to get it working for my purposes.

---

