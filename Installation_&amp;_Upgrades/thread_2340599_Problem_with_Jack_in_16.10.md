---
title: "Problem with Jack in 16.10"
date: 2016-10-20
forum: Installation &amp; Upgrades
---

### Post by lucedan on 2016-10-20
Hello.

I just installed Ubuntu 16.10, the official release.
Very cool, very fast. But I fail to start Jack through qjackctl.


When I try (with Alsa), the error is:


> 22:06:18.100 JACK is starting...
> 
> 22:06:18.104 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2
> 
> connect(2) call to /dev/shm/jack-1000/default/jack_0 failed (err=No
> such file or directory)
> 
> attempt to connect to server failed
> 
> jackd 0.124.1
> 
> Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben
> Hohn and others.
> 
> jackd comes with ABSOLUTELY NO WARRANTY
> 
> This is free software, and you are welcome to redistribute it under
> certain conditions; see the file COPYING for details JACK is running
> in realtime mode, but you are not allowed to use realtime scheduling.
> 
> Please check your /etc/security/limits.conf for the following line and
> correct/add it if necessary:
> 
>   @audio          -       rtprio          99
> 
> After applying these changes, please re-login in order for them to
> take effect.
> 
> You don't appear to have a sane system configuration. It is very
> likely that you encounter xruns. Please apply all the above mentioned
> changes and start jack again!
> 
> 22:06:18.201 JACK was started with PID=11124.
> 
> 22:06:18.205 JACK was stopped
> 
> 22:06:20.235 Could not connect to JACK server as client. - Overall
> operation failed. - Unable to connect to server. Please check the
> messages window for more info.
> 
> connect(2) call to /dev/shm/jack-1000/default/jack_0 failed (err=No
> such file or directory)
> 
> attempt to connect to server failed


and PID is always different.


Does anybody know what's wrong?

---

### Post by lucedan on 2016-10-20
I solved it.

Jack works fine wth the library libjack-jackd2-dev but not with libjack-dev

---

