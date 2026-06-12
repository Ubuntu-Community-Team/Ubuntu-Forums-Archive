---
title: "puppet: manage puppetd with puppet itself"
date: 2010-09-07
forum: Installation &amp; Upgrades
---

### Post by surfer on 2010-09-07
i need to change /etc/default/puppet for my [puppet]("http://www.puppetlabs.com/") clients during the setup of my installation. i wrote a puppet class that checks for changes of the file on the server and restarts puppetd if necessary.

unfortunately: puppet stops puppetd first and does not get to restart it, as the puppet daemon is... well... stopped.

so i shut myself out of all this nice puppetry.

any ideas for a workaround?

---

### Post by surfer on 2010-09-07
i seem to have found a workaround for that:

i just call something like
```

exec{
   "restart_puppet":
       path => "";
       command => "/usr/bin/service puppet restart"
}

```
whenever the file changes.

---

### Post by surfer on 2010-09-07
hmm. no, this does not really work either...

---

### Post by surfer on 2010-09-07
ok, got it:

the parameters in [FONT="Courier New"]/etc/default/puppet[/FONT] are passed to the command line and override everything that is in the config file [FONT="Courier New"]/etc/puppet/puppet.conf[/FONT].

so i remove all the options in [FONT="Courier New"]/etc/default/puppet[/FONT] and just use [FONT="Courier New"]/etc/puppet/puppet.conf[/FONT] as configuration.

that way i can change parameters in [FONT="Courier New"]puppet.conf[/FONT] and send a HUP signal to the [FONT="Courier New"]puppetd[/FONT] process:
```

$ sudo pkill -HUP puppetd

```
this forces the daemon to reread its configuration.


just in case anybody cares... talking to myself here...

---

### Post by surfer on 2010-09-07
once again: no! this does not work. seems to be a [bug]("http://projects.puppetlabs.com/issues/show/793").

i give up and manage puppetd with cron.

---

