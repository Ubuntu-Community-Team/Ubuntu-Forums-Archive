---
title: "Upgrade 10.04 [LTS] Kernel"
date: 2011-08-10
forum: Installation &amp; Upgrades
---

### Post by fleamour on 2011-08-10
Hi

I want to upgrade Lucid kernel to enable TRIM.  I tried this [guide]("http://lightrush.ndoytchev.com/random-1/howtoinstalllinuxkernel2635onubuntu1004lucidfromubuntu1010mavericktheeasyway") but no dice:
```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  linux-headers-generic-lts-backport-maverick: Depends: linux-headers-2.6.35-30-generic but it is not going to be installed
E: Broken packages

```
Anyone know why?

:confused::(:confused:

---

### Post by halj32 on 2011-08-10
have you tried adding ppa:kernel-ppa/ppa to your system's Software Sources, then doing an update.

best if you add this too
you can get it here [http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xA8267963484B044F](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xA8267963484B044F) 
or copy below

-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ESXXeOgEEAL13aaPSn+5Ad/Ob0g+2kq8vxIRefPI8MOeio2/8KacAJDJj6CKsP5CEPz5J
khrLLAY+H0KMwbQhzC2IUtVcpqMp6xHS1S4PP08phLnwebtqusycwH687rCQyRCJpNDpFScO
uI9IiIwUbjnOXVSf1r9uoEFUsAJru7/L4TVqCkCBABEBAAG0I0xhdW5jaHBhZCBQUEEgZm9y
IFVidW50dSBLZXJuZWwgUFBBiLYEEwECACAFAkl13joCGwMGCwkIBwMCBBUCCAMEFgIDAQIe
AQIXgAAKCRCoJnljSEsETxmvA/9hQCxrXCcdrdcVFnJQmW8zFcgzbIFtJGnZvocIpGvQ5E6O
cUy7kQnIoICbaQlydy6Las3vLKqN8M55nZM1LSlACiQmeWvZwIWjrbyIxPYuYJDLbs+jICfj
6azir6Ag7tEAk+nzzKHzbFK6ZhkJve1TGrWeMvKovi7KVTZvJtIt7IkCHAQQAQIABgUCTTBX
TQAKCRC5byMArRHL7mwgD/9CXY6THkZOjaRUykNhVMgQSJyu6wXem1TDitS5SItFxZn9KOtr
iZ1DXIZD5FNBFRfSWy0e2c0/8mRY4PoxV2zEAAj5bygu2Tm2JqdQ468eroCUEQIPMTJq9GR2
1/3yuGwMg83HsZN80bMMkEYOMyywp1h9rFtouyxvN4SlHJ6i3f7mvriABVxmkp7Sz+sTFzBR
+dyQOnalRXKkmxCVqKehdax3012tWgPgcpDrI2UfNYBkylmSsXgsIskWLwFO7Hv1UdXE/IUN
y9qm32cdZDxCc/Q4E5psesJIsyeP4ugsnVhgZSCnetdmVxIAttxG/JXFysp+uWmyQSvPNFS7
6U9sShwcE3Bi0NoGk2P1KKY8bkpWz7PhsIMWHbHQbGntkhh1RsMGy/ZA8SWk/DRWnzOToLZA
7+TtCEBN5bbs9FVpQvlxyTOCKU1qGosjHg4g0h2SWAapQvjiniHdRkfA7eAMEBE/weqlULMJ
g8RSJZ3HTUz4o8hcMJVuVup3axy8UY9lX3f8RhsZXZ5743KUX/SJXyOHYkQ1lo7yRvlw+o/+
SF2HndorCVhdQELnHzY9FSyfPnoH3tC92BUvFHlis6qsT/kfqkKCVP5zvWaLZ2KlZc3+KbyZ
wzUL35n9VzU8m8EoAgEnKjKmlw5irMneKEi6+jg2ZN5Spbx6sJ9dXs8s4g==
=yPGe
-----END PGP PUBLIC KEY BLOCK-----

---

### Post by fleamour on 2011-08-10
Just added ppa exactly as you typed:
 
"ppa:kernel-ppa/ppa"

Still does not work.  

Not sure what to do with key?

---

### Post by ajgreeny on 2011-08-10
In the **Updates** tab of **System-> Administration-> Software sources**, enable the Proposed repositories.  That may help.

---

### Post by fleamour on 2011-08-10
Gently steered in the right direction ajgreeny!  ;););)

Looks like I have to enable backports.  Hope this does not rock the boat where stability is concerned?

---

### Post by halj32 on 2011-08-11
Hi
I would have given full instructions..
but I thought you would have known how to do it.. sorry

  J

---

### Post by fleamour on 2011-08-11
No worries.

:)

---

