---
title: "Need help installing java components"
date: 2008-06-13
forum: Installation &amp; Upgrades
---

### Post by St Stephen on 2008-06-13
Im trying to install anyremote, and for that i need Java WTK.  when i try to install the bin file, i eventually get this:
```

No suitable Java interpreter was detected

0) Specify a path to a Java interpreter directory.
1) Cancel this installation.

```

Ive tried pointing it to gij and then installing, but i eventuall get this:
```
Extracting the installation files...
./sun_java_wireless_toolkit-2_5_2-linux.bin: 466: /usr/bin/jar: not found
Failed to extract files. Installation will stop now.

```

is there a way to use gij for this or do i have to install Java SDK? and if so where should i install the j2sdk bin file?

thanks

---

### Post by oldos2er on 2008-06-13
Install Java from Applications, Add/Remove; or System, Administration, Synaptic Package Manager.

---

### Post by St Stephen on 2008-06-13
aright i installed java-gj-compat and it looked like it worked--
On to bigger and harder problems!

---

### Post by ValentineX on 2010-07-31
A easy tutorial for installing netbeans with mobility in ubuntu ):P

[http://tech.ninja.pk/2010/08/netbeans-j2me-java-mobile-applications-developing-installation-linux/](http://tech.ninja.pk/2010/08/netbeans-j2me-java-mobile-applications-developing-installation-linux/)

---

### Post by nirma1230 on 2011-06-29
To install Java 1.3 for Tivoli and Tivoli Java Client Framework 4.1.1 from the Tivoli desktop, perform the following steps from any Tivoli desktop: 
 
[LIST=1]
[*]From the **Desktop** menu, select **Install &#8594; Install Product** to display the Install Product window.      [IMG]http://publib.boulder.ibm.com/infocenter/tivihelp/v3r1/topic/com.ibm.tivoli.frmwrk.doc/jrecomps.gif[/IMG]
[*]If the **Select Product to Install** list is empty or does not contain **Java 1.3 for Tivoli** and **Tivoli Java Client Framework 4.1.1**, continue with step 3 If the Java components are listed, skip to step 7
[*] Click **Select Media** to display the File Browser window. Use this window to specify the path to the installation image for the Java components.  [IMG]http://publib.boulder.ibm.com/infocenter/tivihelp/v3r1/topic/com.ibm.tivoli.frmwrk.doc/jrepath.gif[/img]
[*]In the **Hosts** list, select the host on which the installation image is mounted.
[*]Navigate to the directory that contains the installation image. The installation directory contains the product index (.IND) file.  Double-click directory names in the **Directories** list until the installation images are shown in the **Files** list.
 Alternatively, if you know the path to the installation image, type the full path in the **Path Name** field. Click **Set Path** to list the contents of the specified directory.
[*]Click **Set Media & Close** to save the path and return to the Install Product window. The window now lists **Java 1.3 for Tivoli** and **Tivoli Java Client Framework 4.1.1**, which indicates that they are available for installation.
[*] In the **Select Product to Install** list, select **Java 1.3 for Tivoli**.
[*]Use the arrow buttons to select the machines on which to install this product. Move the clients from one list (**Available Clients** or **Clients to Install On**) to the other by selecting the client name and clicking the left- or right-arrow button. **Java 1.3 for Tivoli** is installed on the clients in the **Clients to Install On** list.
[*]Click **Install** to install **Java 1.3 for Tivoli**.  The installation process displays a Product Install window similar to the following.
     [IMG]http://publib.boulder.ibm.com/infocenter/tivihelp/v3r1/topic/com.ibm.tivoli.frmwrk.doc/jre001.gif[/IMG]
 
 This window lists the operations that will occur during the installation and any problems that you might want to correct before continuing the installation. If you want to correct any problems, click **Cancel**.
[*]Click **Continue Install** to perform the installation. The Product Install window displays status information as the installation proceeds.  When the installation is complete, the Product Install window displays a completion message and the **Cancel** button becomes the **Close** button.
[*]Click **Close** to close the status window and return to the Product Install window.
[*]In the **Select Product to Install** list, select **Tivoli Java Client Framework 4.1.1**.
[*]Use the arrow buttons to select the Tivoli server or managed nodes on which to install this product. Move the clients from one list (**Available Clients** or **Clients to Install On**) to the other by selecting the client name and clicking the left- or right-arrow button. **Tivoli Java Client Framework 4.1.1** is installed on the clients in the **Clients to Install On** list.
[*]Click **Install & Close** to install **Tivoli Java Client Framework 4.1.1** and close the Install Product window.  The installation process displays a Product Install window, which lists the operations that will occur during the installation and any problems that you might want to correct before continuing the installation. If you want to correct any problems, click **Cancel**.
[*]Click **Continue Install** to perform the installation. The Product Install window displays status information as the installation process proceeds.  When the installation is complete, the Product Install window displays a completion message and the **Cancel** button becomes the **Close** button.
[*]Click **Close** to close the Product Install window.
[/LIST]
Java 1.3 for Tivoli and Tivoli Java Client Framework 4.1.1 are installed. You can now install the Tivoli Software Installation Service depot or client

---

