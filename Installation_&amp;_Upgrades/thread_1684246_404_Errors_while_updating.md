---
title: "404 Errors while updating"
date: 2011-02-08
forum: Installation &amp; Upgrades
---

### Post by Splat_NJ on 2011-02-08
I went to update today and got these errors. Anyone else getting these?:

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/libnautilus-extension1_2.32.0-0ubuntu1.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/libnautilus-extension1_2.32.0-0ubuntu1.2_i386.deb) 404  Not Found [IP: 91.189.88.46 80]

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus-data_2.32.0-0ubuntu1.2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus-data_2.32.0-0ubuntu1.2_all.deb) 404  Not Found [IP: 91.189.88.46 80]

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus_2.32.0-0ubuntu1.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus_2.32.0-0ubuntu1.2_i386.deb) 404  Not Found [IP: 91.189.88.46 80]


Now, what can I do to resolve this?

---

### Post by Old_Grey_Wolf on 2011-02-08
It looks like the server you are using is not responding.

Get into Synaptic Package Manager and go to the menu "Settings > Repositories"; then, select "Other..." from the "Download from:" menu. Then click on the "Select Best Server" button. It will take some time for Synaptic to test the servers and give you a suggested server. When it does, click the "Choose Server button". Then follow the instructions to Reload.

Then try updating again.

Many times the problem will resolve itself after a few hours or days when the server has been updated or the network/server problem resolved. I wasn't able to find 91.189.88.46 80 in a whois lookup; therefore, I thinks it has some problems.

---

### Post by Splat_NJ on 2011-02-08
Thank you, Old Gray Wolf. That did the trick.

---

