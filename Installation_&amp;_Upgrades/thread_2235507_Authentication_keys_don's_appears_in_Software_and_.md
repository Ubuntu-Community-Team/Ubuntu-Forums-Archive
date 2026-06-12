---
title: "Authentication keys don's appears in Software and Updates."
date: 2014-07-21
forum: Installation &amp; Upgrades
---

### Post by hectorsales on 2014-07-21
Hi, I made a clean install of Ubuntu 14.04, and have added some external repositories (Virtualbox, Spotify, Google-Chrome .. etc), the repositories have been added to 

```
/etc/apt/sources.list.d
```


> ubu40@trusty:/etc/apt/sources.list.d$ ls
atareao-atareao-trusty.list
atareao-atareao-trusty.list.save
google-chrome.list
google-chrome.list.save
maarten-baert-simplescreenrecorder-trusty.list
maarten-baert-simplescreenrecorder-trusty.list.save
mc3man-trusty-media-trusty.list
mc3man-trusty-media-trusty.list.save
noobslab-apps-trusty.list
noobslab-apps-trusty.list.save
oibaf-graphics-drivers-trusty.list
oibaf-graphics-drivers-trusty.list.save
pipelight-stable-trusty.list
pipelight-stable-trusty.list.save
spotify.list
spotify.list.save
thebernmeister-ppa-trusty.list
thebernmeister-ppa-trusty.list.save
virtualbox.list  


If I open Software and Updates in the Authentication tab doesn't appears the keys ..


[B]Screenshot: Other Software

[/B]
[[IMG]http://i273.photobucket.com/albums/jj229/hectorsales/Softwareyactualizaciones_002_zps902952e1.png[/IMG]]("http://s273.photobucket.com/user/hectorsales/media/Softwareyactualizaciones_002_zps902952e1.png.html")



**Screenshot: Authentication tab**



[[IMG]http://i273.photobucket.com/albums/jj229/hectorsales/Softwareyactualizaciones_001_zps90ad28ee.png[/IMG]]("http://s273.photobucket.com/user/hectorsales/media/Softwareyactualizaciones_001_zps90ad28ee.png.html")


Anyone know what is happening ?8-[ 

Best Regards,
 
Héctor.

---

### Post by ajgreeny on 2014-07-21
Did you add these repos with the ```
sudo add-apt-repository
``` command or manually?

Only doing it with the command will add the security authorities to the system, though you should be able to add the authentication keys manually but we will need to have the error message details for that.

See [https://help.ubuntu.com/community/Repositories/Ubuntu#Authentication_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Authentication_Tab) for all the details.

---

### Post by hectorsales on 2014-07-21
Thanks @jgreeny for you reply, i added these repos with the command that you describe above.  I have discovered one thing that has left me surprised: 

**If I open synaptic ---> configuration ---> Repositories ¡¡¡ The keygen appears !!!**.:shock::shock: 


[[IMG]http://i273.photobucket.com/albums/jj229/hectorsales/Seleccioacuten_003_zps0f0409eb.png[/IMG]]("http://s273.photobucket.com/user/hectorsales/media/Seleccioacuten_003_zps0f0409eb.png.html")



....but if open[B] the Software Updates through the dash the keygens doesn't appears.
[/B]

[[IMG]http://i273.photobucket.com/albums/jj229/hectorsales/Aacutereadetrabajo1_004_zps5b0002a8.png[/IMG]]("http://s273.photobucket.com/user/hectorsales/media/Aacutereadetrabajo1_004_zps5b0002a8.png.html")



[[IMG]http://i273.photobucket.com/albums/jj229/hectorsales/Softwareyactualizaciones_001_zps90ad28ee.png[/IMG]]("http://s273.photobucket.com/user/hectorsales/media/Softwareyactualizaciones_001_zps90ad28ee.png.html")



**A picture is worth a thousand words: **



[[IMG]http://i273.photobucket.com/albums/jj229/hectorsales/Seleccioacuten_005_zps5610b82a.png[/IMG]]("http://s273.photobucket.com/user/hectorsales/media/Seleccioacuten_005_zps5610b82a.png.html")



I can not find logic to what is happening ...:shock:](*,)


Best Regards,

Héctor

---

### Post by ajgreeny on 2014-07-22
Sorry, I don't use unity and never use the update-manager; synaptic every time for me, whether installing, uninstalling, updating or whatever, so I have absolutely no idea why there is a difference between the authorisations showing in the two update utilities.

---

