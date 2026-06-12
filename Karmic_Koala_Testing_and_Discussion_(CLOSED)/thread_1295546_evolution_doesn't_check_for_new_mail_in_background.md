---
title: "evolution doesn't check for new mail in background"
date: 2009-10-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mgvbstar on 2009-10-19
i'm using the karmic beta. when i have the evolution mail window open and i receive a new message, the indicator applet icon changes to alert me of the new message. however, when i close the evolution mail window, not quit the application, and i receive a new email the indicator applet icon doesn't change. i have evolution set to check to new messages every 5 minutes but even after waiting 20 minutes the applet icon doesn't change.

This is what is running after i close the evolution window:
```
[0]~$ ps ax | grep evolution
 2032 ?        Sl     0:00 /usr/lib/evolution/2.28/evolution-alarm-notify
 2179 ?        Sl     0:00 /usr/lib/evolution/evolution-data-server-2.28 --oaf-activate-iid=OAFIID:GNOME_Evolution_DataServer_BookFactory:1.2 --oaf-ior-fd=26
 8270 ?        Sl     0:00 /usr/lib/evolution/2.28/evolution-exchange-storage --oaf-activate-iid=OAFIID:GNOME_Evolution_Exchange_Connector_BookFactory:1.2 --oaf-ior-fd=34
25603 pts/3    S+     0:00 grep evolution

```

what could be wrong?

---

### Post by mohegan on 2009-10-19
When you close the application main window, evolution is closed (not like empathy).
The 3 processes don't check new mail.

If you want check email without evolution main window, you can install mail-notification and configure it to check your email (not with evolution parameter because it doesn't work). It send notifications and add an icon in the notification area when you have new mails.[IMG]http://server-pro.com/poptrayminus/poptray-minus_in_the_tray.png[/IMG]
You can run mail-notification at startup with this command (add to gnome startup programs) : 
```
sh -c "sleep 30 && mail-notification&"
```
[IMG]http://pollycoke.files.wordpress.com/2006/06/mailnotification.jpg[/IMG]

Site : [http://www.nongnu.org/mailnotify/]("http://www.nongnu.org/mailnotify/")

---

