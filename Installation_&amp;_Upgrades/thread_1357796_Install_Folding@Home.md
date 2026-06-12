---
title: "Install Folding@Home"
date: 2009-12-17
forum: Installation &amp; Upgrades
---

### Post by DTHCND on 2009-12-17
I just made a script to install folding@home for my friend and thought might as well release it to the public at the same time.

 So all you have to do is download the the file extract it to your desktop... (MUST BE DESKTOP!) then follow the read me in the folder.
 
 Also please remember this is ONLY tested on Ubuntu but may work on other gnome based systems.

Download from: [http://www.mediafire.com/?yi54gqhzzgm](http://www.mediafire.com/?yi54gqhzzgm)

Please leave feedback.

Edit: This script will create a dedicated system user on your machine to run the process and store the data. Data will be stored in a subfolder of /var/ (This system user will not be assigned a login, password or shell for security reasons.) The application will be handled with an init service for automatically starting at boot and allowing you to stop or start the service on demand. And will never require any input from the user (except during installation).

---

