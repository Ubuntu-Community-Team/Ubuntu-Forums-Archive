---
title: "Problems with Ubuntu 18.04 on virtual hosting service"
date: 2018-05-11
forum: Installation &amp; Upgrades
---

### Post by rolfmblindgren on 2018-05-11
I've run into quite a snag. I'm running an Ubuntu system with a virtual service provider, so there are limits to what I can do.  I have access to a Ubuntu 16.04 rescue disk. 

The way this has workeds, is I've been able to boot the rescue disk, mount the virtual hosted system, and start services from it. And sort of play with the system to make it bootable.

What happens now, is this: I start the virtual server, enter the rescue menu, and try to mount the file systems.

This happens.

[IMG]https://lh3.googleusercontent.com/elb5QLKCI9znc5-ShPpB3kd-CH3hogjBR37qpeUTx_krl-dEXhPZB4gun9aG12gtPNSkeOsXYAaCcA4x9fdhOL2Zor4t8MOr2t7NsTvQgcUyJL8wbYOlgwkDWTsWZGHTo9gSGRLjjETFFIjsFXwgBb_wahcdoAW-q7HB-Y6BEyvTyRewRVxOykdTtZEspAYCqx8QG0mUM24U81D7Ncx00nUDYF7QQz0js_HGNPSoGm2InWAnpz7kIDJsmHD0hECoFyaP0mbUfmwtfOCdfvO8mriNPb_XLGD8h4mUAAekOsv4ggPPSFhwAquH-RVQqr4ylWNSztm2-7xqHgjnfUJhvyMJvFkobxoSu6y9-V-KIYVegKcuMAMfTK8x62XSpSbBypRV0UscK3TvacSZtyAUTbh2gzcH0pgd6Hs5spz4LzcxMQTtUrLEfmAb-Oze4DVXfmJOECNmwEmh7eAYiCjgwULZIgrhXOLMpKpzduuZvQQ9nRfpiMj4qoXSkATpD-nxSmn7swYfLNxCAiDe1-EXE6xXWjo5qFA0B9RUEzZvmUggD1MgqMHX6w0mllK_J34dfF-0Aoha4UgSLMT6LHRPoiXnu5C01OsOZi7XBCeyq2_0jk71OWS04J7251Bp3uRWLAEu5AOloAI2glbSYtK6yQcIHkqizRgc=w871-h237-no[/IMG]
This used to work. But what happens now, is this:
[IMG]https://lh3.googleusercontent.com/V_qC7aV-4eboyuciV2W70z7G-8porpxgWjphGDmovML2eDXkekYCZZ9736RIsQCnn88nKAtu8_7aSaqPzFtx_UKp1zw3yz7pkwCvYYii6jNqkq4WqOT0xlC5J6zWxXi3pQh6y8uckU8M1BbPHdGBY9A3O-KrKGWVr8PO3cCk-LwkZ4mua_fE8OXE1pbVa4g3hRyJN_Ql-Ow537Bkg5MhQ4ZlobswaRQnjL2FS8722QZPmdRNneORlOlUzbHMUMsAUcXmcbgbDT4AA649RvhjkU4NhiN4E8s_0AdOc_QkYq_Xpr9IRgDcikDinc8TM9LbIlxfgU9cxNrUl629Zp-lFSlDp1ciOGXLnwJen3YaHc191AAQmLNLnFgEs1HgydiQYt6mm8ge_CT708qxRLFhL13lRsiyW-QDP7bz1lhn_a9EiN5CZANzqRgnmDShT7wv4-KZSkmBhY4IslZUXw2DvCvUhE0B29RJ93NY5i1gCHmsOZ_gm54f1u11TZ7_Lw4d34wk7yqIZBEHVIjEVdMhslIinifj1EZJF4JKZtpgrriP_iXyhAGuKeq5NE1LGkceJPlpPwVU1AFpun3szaI03LkZEH_qbz5dbuoq-mGpEin0gzH5Yx8iyyeza0iXeA45sggpNtxvV5DByk0RNYrAjxmZk-b0S422=w935-h303-no[/IMG]

If i choose to "Execute a shell in the installer environment", I can see this:

[IMG]https://lh3.googleusercontent.com/n5Mh21nYaYeat5MXZv8CTTbbY4guP4oCgFnNauKOrQ1bj3azKkR0dJZgCtOqIyu8AdTBoyKXoCCeqDIo2LMfTolvvK0Pwbk3RV-D8C30DyJuJBzqH9oJ0-dY8bX-vphnmwD8Qr1fivvEm70put0nDm00LecrnRgNUBQgkJQkAlj-gVOFoWoiDH23Rp5_RZfoKLXDVv663-vZkk6kmry2-vMegE-HB6vA_3uSVbtz9VQYygtbkwbYZeINXkfauM8GVmND-3PJq2Qd8eajbDAFoWfN79fp_reEOBuotDSY2VL5iuOP7fyweodfDEtR-AujtGD4uJy4P5XJOliMq_yDJR8gE10sH9gas2Zoff3MMWaT7wLXHeguua8hZgyDLq_RQHF-9tMQeob19mc50Y9IdI6BMdv41qRSSMHesexgW1DsozdoJfAzGjuvDiWII5CKWaFPYxzywd_nsJSdaUtUsaswF_BLbJtSlGtcqVVIBxUfYLXLmRf2_AsydZvGJK81VEz7Eam4X8P3_h6I6HATQXNh19Svwn1X6KuasVUgBEDb18Pils28Y4qa91HGP7OR6pbL3XC9CQHrg8kFbzwzI5ECWj1QAyRN15IhTM7sHPufnv_zwhhK6UqXYitSRMuP7kbZ49EWOMp8ymCiByBSpOZrqmjuAM7D=w894-h188-no[/IMG]

So the disks are there, mounted to /target.  But can't be mounted to /, as I understand it.

What can I do to fix this and at least be able to mount the disks properly?

Any and all hints & tips appreciated.

Thank you,

---

