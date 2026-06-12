---
title: "preseed-auto with dhcp"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by michael-wd21 on 2010-05-05
Hi,

I am having a problem using an http-delivered preseed file to install Lucid server x86_64 (on a KVM guest).

I've remastered the Lucid ISO with the following in isolinux/text.cfg:

```
append  auto=true priority=critical url=eagle initrd=/install/initrd.gz quiet --
```I found I couldn't just use:

```
auto url=eagle
```as documented in the installation guide, but I've read that what I have is equivalent - and this seems to be true.

I have a DHCP server configured to send the filename option for this client, and a web server where my preseed is stored. I've tested my preseed file with:

```
debconf-set-selections -c tonal.preseed
```and I get no errors.

When I boot my guest, it proceeds as expected to configuring the network without asking the usual questions (actually it persists in wanting me to choose my language and press enter at the boot menu, but I can live with that just now). DHCP configuration succeeds and it goes on to download the preseed file. It then throws an error:

```
Failed to retrieve the preconfiguration file

The file needed for preconfiguration could not be retrieved from
eagleThe installation will proceed in non-automated mode
```My web server, which is the KVM host (eagle), disagrees:
```

192.168.0.130 eagle - [06/May/2010:00:00:51 +0100] "GET /d-i/tonal.preseed HTTP/1.1" 200 3043 "-" "Wget"

```and in fact /var/lib/preseed/log contains my preseed!

If I select to configure the network again, the error changes to:


```
Failed to retrieve the preconfiguration file

The file needed for preconfiguration could not be retrieved from
http://eagle/d-i/tonal.preseed
http://eagle/d-i/tonal.preseed The installation will proceed in
non-automated mode
```and this time my web server agrees:

```

192.168.0.130 - - [06/May/2010:00:04:54 +0100] "GET /d-i/tonal.preseed\nhttp://eagle/d-i/tonal.preseed HTTP/1.1" 400 349 "-" "-"

```This looks like a bug to me. Has anyone managed to get this working?

Cheers

Michael

---

