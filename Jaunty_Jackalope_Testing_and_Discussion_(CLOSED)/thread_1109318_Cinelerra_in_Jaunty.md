---
title: "Cinelerra in Jaunty"
date: 2009-03-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by mangloid on 2009-03-28
I am trying to get this compiled in Jaunty, everything is found except:

  OpenGL 2.0 libraries    missing
Hardware acceleration using OpenGL 2.0 is disabled



What is the correct library missing to compile this? Has anyone else successfully compiled cinelerra in Jaunty?

---

### Post by altonbr on 2009-03-29
This guy has Cinelerra in his PPA for Jaunty: [https://launchpad.net/~capitanterrex/+archive/ppa](https://launchpad.net/~capitanterrex/+archive/ppa)

---

### Post by GARoss on 2009-03-29
> **altonbr said:**
> This guy has Cinelerra in his PPA for Jaunty: [https://launchpad.net/~capitanterrex/+archive/ppa](https://launchpad.net/~capitanterrex/+archive/ppa)

I'm fairly new to Ubuntu & need to ask lots of questions. Do I copy & paste *[https://launchpad.net/~capitanterrex/+archive/ppa](https://launchpad.net/~capitanterrex/+archive/ppa)* into **System/Administration/Software Sources/Third-Party Software, +Add** or is it more complicated than that? Will Cinelerra appear in Synaptic Package Manage afterwards?
Thanks

---

### Post by zekopeko on 2009-03-29
> **GARoss said:**
> I'm fairly new to Ubuntu & need to ask lots of questions. Do I copy & paste *[https://launchpad.net/~capitanterrex/+archive/ppa](https://launchpad.net/~capitanterrex/+archive/ppa)* into **System/Administration/Software Sources/Third-Party Software, +Add** or is it more complicated than that? Will Cinelerra appear in Synaptic Package Manage afterwards?
Thanks

you got it right. don't forget to reload/refresh synaptic.

---

### Post by binbash on 2009-03-29
> **altonbr said:**
> This guy has Cinelerra in his PPA for Jaunty: [https://launchpad.net/~capitanterrex/+archive/ppa](https://launchpad.net/~capitanterrex/+archive/ppa)

I am gonna try that packages, thanks

---

### Post by GARoss on 2009-03-30
> **zekopeko said:**
> you got it right. don't forget to reload/refresh synaptic.

Well, I opened **System/Administration/Software Sources/Third-Party Software, +Add** pasted *[https://launchpad.net/~capitanterrex/+archive/ppa](https://launchpad.net/~capitanterrex/+archive/ppa)* & wasn't given **+Add**; it stayed under-intensified & would not allow. Then I tried *deb [http://ppa.launchpad.net/capitanterrex/ppa/ubuntu](http://ppa.launchpad.net/capitanterrex/ppa/ubuntu)* & that didn't work either. 
What am I doing wrong?:confused:

---

### Post by skintythe1andonly on 2009-03-30
u almost have it, try

```
deb http://ppa.launchpad.net/capitanterrex/ppa/ubuntu intrepid main
```

you can change intrepid to hardy or whatever you have installed.

---

### Post by GARoss on 2009-03-31
This is the error I got;
*W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0E931CE221789C97*
after pasting 
*deb [http://ppa.launchpad.net/capitanterrex/ppa/ubuntu](http://ppa.launchpad.net/capitanterrex/ppa/ubuntu) jaunty main*
as an +ADD.
I had all this set-up while working in Kubuntu Jaunty & now I have deleted it when Ubuntu jaunty was installed over it. Is there a way to retrieve the Pubkey or do I need to reapply?

---

### Post by ZarathustraDK on 2009-04-23
You need to add the pgp-key for the ppa in order to have secure access to his repository. Usually you do this by clicking your way to the authors launchpad-page and find it there. Capitanterrex's pgp-key is :
```
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ESX3RMgEEAKuh19NE6MVmBZ8fxTyjgCTRT2i77yHHseOdJAAglIbsWTuFzAmrLPlTCtP9
XgVDzODlGHCyelnzILs2/nH0CDubxnyY+4tJYNq8b2sz2rG1k6pdwlBd8YaFaumpKLS64cZ8
jEWT2eSqh5pG8wR8EJIoEqE/+HbRXaa2YkrWey6tABEBAAG0LkxhdW5jaHBhZCBQUEEgZm9y
IEd1aWxsZXJtbyBHdXRpw6lycmV6IEhlcnJlcmGItgQTAQIAIAUCSX3RMgIbAwYLCQgHAwIE
FQIIAwQWAgMBAh4BAheAAAoJEA6THOIheJyX+FYD/RyY6zP30vEw8hJoeIUxLMCJKkrkLE7c
w89PJmBn4yuQaRFnlH9iZLtNgNYTtQHKpbPVfMo1JTLECVejsPIm5Gc7ulRdtdjHm1s1N0df
5Py9cEpxYnicR+5LDXNMOexYFbv+oFpAqIIAOC/49rFiBLu2o7FFDANYWajiffMafbHC
=KM8L
-----END PGP PUBLIC KEY BLOCK-----

```

Copy/paste it into an empty textfile and save it. Then add the key with Administration-->Software Sources-->Authentication-tab (I think it's called). Then refresh synaptic with the ppa-repo added, you should now be able to install cinelerra.

This is standard-procedure for ppa-repos, very nice to have ingrained on the spine if you dabble in bleeding edge stuff/stuff with no official debs for it.

---

