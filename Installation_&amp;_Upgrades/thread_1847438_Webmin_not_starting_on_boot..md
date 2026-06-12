---
title: "Webmin not starting on boot."
date: 2011-09-20
forum: Installation &amp; Upgrades
---

### Post by astroboy123 on 2011-09-20
Hey,

I installed webmin (by synaptic or i think i downloaded the .deb from the their website)

The problem is the service doesn't start upon boot.

I know it use too... but i'd like to know where is the locations of the script/s that runs at boot to start this service.

i thought it would be something like /etc/init.d or /etc/rc0.d

i'd like to find this script or its known locations on a default install so that i can see if anything has changed.

Would someone be able to paste this default script here so that i can copy it and place back in the correct location so that i can have this service run at boot.

I can get it to work now by running sudo /etc/webmin/start

Webmin version:1.550

EDIT-
In webmin it's self it says that its starts on boot but it's not running

This is the scirpt copied from webmin:

# webmin
#
# Webmin

description  "Webmin"

start on runlevel [2345]
stop on runlevel [!2345]

pre-start script
    1

end script

exec /etc/webmin/start

But still the service doesn't start on boot...

EDIT-
I've had a look through the /var/log/daemon.log

and the process never starts but it does say that "webmin was terminated with status 127"

what does this mean?

i think it tries to start but cant for some reason....

Thanks in advance.

---

### Post by n1v0la on 2011-12-09
Hello astroboy123.

In my Kubuntu 11.10 the webmin config is indeed /etc/init.d/webmin.
Please see attached file.

I also have the matching s01webmin in the rc directories
  /etc/rc2.d
  /etc/rc3.d
  /etc/rc5.d

Hope this helps.

---

