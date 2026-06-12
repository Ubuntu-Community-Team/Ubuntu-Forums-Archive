---
title: "[intrepid] nm-applet + wpa2 + TLS-EAP-MSCHAPv2"
date: 2008-10-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by iraiscoming223 on 2008-10-27
Hello everybody!
I've switched from Hardy to Ibex far before the RC, and since then I have had problems with the wireless and WPA2 networks.
I'm used to connect to my Campus wireless network via nm-applet, using WPA2, TLS, my asi.cer certificate and my Cert.p12 key, with my anonymous identity and private key password. That worked flawlessly in Hardy. Now, when I try to connect to the wireless network (apart the fact that the GUI is really different) and I fill the form, the "Connect" button keeps stayin' grey (not activated).. :confused:
I've played around with it for a while and found out that nm tries to check whether a certificate/key file is valid or not, and then activate the button dynamically. I'm almost sure that I've set up the connection as I did in Hardy, so... what's wrong?!

N.B.(I've seen lot of people on launchpad complying about a bug with some wireless cards and nm-applet, and tried out their debs, but I couldn't get rid of the problem...)

Thanks in advance,
Marco

---

