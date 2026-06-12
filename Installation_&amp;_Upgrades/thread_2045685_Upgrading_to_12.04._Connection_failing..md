---
title: "Upgrading to 12.04. Connection failing."
date: 2012-08-21
forum: Installation &amp; Upgrades
---

### Post by chrisinspace on 2012-08-21
I'm trying to upgrade a machine from 10.04 to 12.04.  Every method I have tried has resulted in the same error. I start the process and while trying to fetch the new packages, I get multiple "Connection failed" errors. I don't get any errors when I 'apt-get update' and all of the new packages are downloading fine except linux-firmware and linux-image.  Here's a sample of some of the errors from last time:

```
                                     
Err http://archive.ubuntu.com/ubuntu/ precise/main linux-firmware all 1.79     
  Connection failed [IP: 91.189.92.183 80]                                     
Err http://archive.ubuntu.com/ubuntu/ precise-updates/main linux-image-3.2.0-29-generic amd64 3.2.0-29.46
  Connection failed [IP: 91.189.92.188 80]                                     
Err http://archive.ubuntu.com/ubuntu/ precise-security/main linux-image-3.2.0-29-generic amd64 3.2.0-29.46
  Connection failed [IP: 91.189.92.190 80]                                     

```

I've tried from a GUI (update-manager -d), from the command line (do-release-upgrade d), and using the cdrom (./cdromupgrade).  They all result in this error.  I have attempted the upgrade several times since last Friday, but still can't connect.  Does anyone have any idea what's going on here?

---

### Post by chrisinspace on 2012-08-21
My latest attempt just failed.  Here's the error output:

```
The upgrade has aborted. Please check your Internet connection or 
installation media and try again. All files downloaded so far have 
been kept. 

Failed to fetch 
http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-3.2.0-29-generic_3.2.0-29.46_amd64.deb 
Connection failed [IP: 91.189.92.189 80] 
Failed to fetch 
http://archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.79_all.deb 
Connection failed [IP: 91.189.92.189 80] 


Restoring original system state

```

---

### Post by chrisinspace on 2012-08-23
Still troubleshooting.  I ran this command:

```
cd && wget http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-3.2.0-29-generic_3.2.0-29.46_amd64.deb
```

and got this result:

```
--2012-08-23 17:23:35--  http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-3.2.0-29-generic_3.2.0-29.46_amd64.deb
Resolving us.archive.ubuntu.com... 91.189.91.31, 91.189.91.13, 91.189.91.14, ...
Connecting to us.archive.ubuntu.com|91.189.91.31|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 38540402 (37M) [application/x-debian-package]
Saving to: `linux-image-3.2.0-29-generic_3.2.0-29.46_amd64.deb.1'

100%[======================================>] 38,540,402  11.0M/s   in 3.4s    

2012-08-23 17:24:28 (10.8 MB/s) - `linux-image-3.2.0-29-generic_3.2.0-29.46_amd64.deb.1' saved [38540402/38540402]

```

It looks like the connection succeeded and the file was downloaded.  I still can't figure out why the upgrade won't work.  Please help...

---

### Post by chrisinspace on 2012-08-24
Well, after sorting through the mountain of helpful advice in all of those replies I received, I finally found a solution myself.

I downloaded the 12.04**.1** ISO and ran ./cdromupgrade from that.  I then was able to decline downloading any further packages (this caused the installation to terminate when using the older 12.04 disk).  The upgrade then bypassed "Getting new packages" and went straight to "Installing the upgrades".

If you run into this problem, you can get the .1 disk here:

[http://releases.ubuntu.com/12.04.1](http://releases.ubuntu.com/12.04.1)

---

