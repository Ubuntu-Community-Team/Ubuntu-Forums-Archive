---
title: "apache 2.2.9-3 = broken IPv6 access?"
date: 2008-08-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by David Tomic on 2008-08-27
Hi all ... I'm back with another problem! ;)

Since applying the latest Apache update [2.2.9-3ubuntu1], I've noticed that I can no longer seem to access my webserver using IPv6 anymore.

If I try loading the address in a browser, then I just get a message saying:

> Failed to Connect

Firefox can't establish a connection to the server at [2001:44b8:61::c5].

Though the site seems valid, the browser was unable to establish a connection.

Any clues as to what the problem might be ... or how I might go about finding a solution?

Any help much appreciated!

---

### Post by dinxter on 2008-08-27
you could look at the log files in /var/log/apache2/ for info and perhaps the changelogs in /usr/share/doc/apache2/ and /usr/share/doc/apache2-mpm-prefork/ (if you use that version) to see if any of the changes might have affected your setup.
just for the record, ipv6 through firefox to the same version of apache seems fine here

---

### Post by dinxter on 2008-08-27
i stand corrected, ipv4 works fine and ipv6 works fine on localhost only, ipv6 is unreachable from outside the server machine. dont know if it was before the upgrade but i'll look into it and let you know if i find something

[EDIT] Mine turns out to be a cheap router problem and not apache itself so i doubt i can help you much

---

### Post by David Tomic on 2008-08-27
> **dinxter said:**
> i stand corrected, ipv4 works fine and ipv6 works fine on localhost only, ipv6 is unreachable from outside the server machine. 

Yeah ... mine doesn't work trying to access it locally either.  Same error message.

This morning though, update manager is telling me that there's another upgrade for Apache [2.2.93-ubuntu2], so I'm hoping that might help.

I can't install it yet though, because it's still got an unresolved dependency with apache2-mpm-prefork ...

---

