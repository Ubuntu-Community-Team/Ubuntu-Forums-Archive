---
title: "ssh:connection timed out"
date: 2012-04-17
forum: Installation &amp; Upgrades
---

### Post by itba on 2012-04-17
I am trying the following command on ubuntu 
  ```
ssh host@xx.xx.xxx.xxx
```  and I get the following error:
  ```
ssh: connect to host xx.xx.xxx.xxx port 22: Connection timed out
```  so, I tried the following:
  ```
telnet xx.xx.xxx.xxx 22xx
```  and I got the following message:
  ```
Trying xx.xx.xxx.xxx...
Connected to xx.xx.xxx.xxx.
Escape character is '^]'.
SSH-2.0-OpenSSH_5.5
Connection closed by foreign host.
```  Can anyone help me understand what the problem is and how I can fix it.

---

### Post by mikaelcrocker on 2012-04-17
Is this the first time you've tried connecting to it? Is port 22 open on the server, netstat command will help there.

Also do you have ssh keys? Are they in the right place?  i.e. ~/.ssh

---

### Post by itba on 2012-04-17
Is this the first time you've tried connecting to it? [COLOR=Blue]**Yes**[/COLOR]

Is port 22 open on the server, netstat command will help there.[COLOR=Blue] **running netstat returns something to the effect of :**[/COLOR]
```
-6de-0-4428e96bd2c09
unix  3      [ ]         STREAM     CONNECTED     22071    
unix  3      [ ]         STREAM     CONNECTED     22070    /tmp/orbit-ba/linc-4f9-0-d667b0313e79
unix  3      [ ]         STREAM     CONNECTED     21206    
unix  3      [ ]         STREAM     CONNECTED     22061    @/tmp/.ICE-unix/1203
unix  3      [ ]         STREAM     CONNECTED     22060    
unix  3      [ ]         STREAM     CONNECTED     21197    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     22058    
unix  3      [ ]         STREAM     CONNECTED     19442    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     20265    
unix  3      [ ]         STREAM     CONNECTED     14858    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     15678    
unix  2      [ ]         DGRAM                    15593    
unix  3      [ ]         STREAM     CONNECTED     14392    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     15384    
unix  3      [ ]         STREAM     CONNECTED     14385    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     14384    
unix  3      [ ]         STREAM     CONNECTED     14380    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     14313    
unix  3      [ ]         STREAM     CONNECTED     14378    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     14377    
unix  3      [ ]         STREAM     CONNECTED     14310    /tmp/orbit-ba/linc-641-0-400188725b0e7
unix  3      [ ]         STREAM     CONNECTED     14376    
unix  3      [ ]         STREAM     CONNECTED     14375    /tmp/orbit-ba/linc-4f9-0-d667b0313e79
unix  3      [ ]         STREAM     CONNECTED     14308    
unix  3      [ ]         STREAM     CONNECTED     14368    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     14297    
unix  3      [ ]         STREAM     CONNECTED     13273    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     13272    
unix  3      [ ]         STREAM     CONNECTED     13225    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     14097    
unix  3      [ ]         STREAM     CONNECTED     13163    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     14029    
unix  3      [ ]         STREAM     CONNECTED     14028    /tmp/orbit-ba/linc-634-0-51e3821962152
unix  3      [ ]         STREAM     CONNECTED     13162    
unix  3      [ ]         STREAM     CONNECTED     13161    /tmp/orbit-ba/linc-4f9-0-d667b0313e79
unix  3      [ ]         STREAM     CONNECTED     14026    
unix  3      [ ]         STREAM     CONNECTED     13147    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     14013    
unix  3      [ ]         STREAM     CONNECTED     13080    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13079    
unix  3      [ ]         STREAM     CONNECTED     13074    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     13073    
unix  3      [ ]         STREAM     CONNECTED     13071    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     13982    
unix  3      [ ]         STREAM     CONNECTED     13067    /tmp/orbit-ba/linc-61b-0-7b403a784a462
unix  3      [ ]         STREAM     CONNECTED     13977    
unix  3      [ ]         STREAM     CONNECTED     13976    /tmp/orbit-ba/linc-4f9-0-d667b0313e79
unix  3      [ ]         STREAM     CONNECTED     13065    
unix  3      [ ]         STREAM     CONNECTED     13054    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     13053    
unix  3      [ ]         STREAM     CONNECTED     13049    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     13048    
unix  3      [ ]         STREAM     CONNECTED     13045    /tmp/orbit-ba/linc-611-0-52f90ebc36b9c
unix  3      [ ]         STREAM     CONNECTED     13044    
unix  3      [ ]         STREAM     CONNECTED     13042    /tmp/orbit-ba/linc-4f9-0-d667b0313e79
unix  3      [ ]         STREAM     CONNECTED     13041    
unix  3      [ ]         STREAM     CONNECTED     13013    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     13937    
unix  3      [ ]         STREAM     CONNECTED     12998    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     13932    
unix  3      [ ]         STREAM     CONNECTED     12993    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     12992    
unix  3      [ ]         STREAM     CONNECTED     12958    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     12956    
unix  3      [ ]         STREAM     CONNECTED     12957    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     12955    
unix  3      [ ]         STREAM     CONNECTED     13920    /home/ba/.pulse/ceca739e94a5ded55a826c900000000b-runtime/native
unix  3      [ ]         STREAM     CONNECTED     13919    
unix  3      [ ]         STREAM     CONNECTED     12944    /tmp/orbit-ba/linc-61a-0-69a5b41713461
unix  3      [ ]         STREAM     CONNECTED     12943    
unix  3      [ ]         STREAM     CONNECTED     12941    /tmp/orbit-ba/linc-4f9-0-d667b0313e79
unix  3      [ ]         STREAM     CONNECTED     12940    
unix  3      [ ]         STREAM     CONNECTED     13892    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     12911    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     12910    
unix  3      [ ]         STREAM     CONNECTED     13890    
unix  3      [ ]         STREAM     CONNECTED     12907    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13889    
unix  3      [ ]         STREAM     CONNECTED     13888    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     13887    
unix  3      [ ]         STREAM     CONNECTED     12897    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     12896    
unix  3      [ ]         STREAM     CONNECTED     13835    /tmp/orbit-ba/linc-600-0-69200e10e91e9
unix  3      [ ]         STREAM     CONNECTED     12856    
unix  3      [ ]         STREAM     CONNECTED     12855    /tmp/orbit-ba/linc-4f9-0-d667b0313e79
unix  3      [ ]         STREAM     CONNECTED     13833    
unix  3      [ ]         STREAM     CONNECTED     12789    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     13793    
unix  3      [ ]         STREAM     CONNECTED     13770    @/dbus-vfs-daemon/socket-7xEhD48R
unix  3      [ ]         STREAM     CONNECTED     12786    
unix  3      [ ]         STREAM     CONNECTED     13769    @/dbus-vfs-daemon/socket-6UIJv6UR
unix  3      [ ]         STREAM     CONNECTED     12785    
unix  3      [ ]         STREAM     CONNECTED     12781    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     13764    
unix  3      [ ]         STREAM     CONNECTED     13696    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     13695    
unix  3      [ ]         STREAM     CONNECTED     12742    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12741    
unix  3      [ ]         STREAM     CONNECTED     12721    @/dbus-vfs-daemon/socket-sp6tKMQn
unix  3      [ ]         STREAM     CONNECTED     12720    
unix  3      [ ]         STREAM     CONNECTED     12719    @/dbus-vfs-daemon/socket-SPcko2zB
unix  3      [ ]         STREAM     CONNECTED     12718    
unix  3      [ ]         STREAM     CONNECTED     13615    @/dbus-vfs-daemon/socket-7GnOg2Px
unix  3      [ ]         STREAM     CONNECTED     13609    
unix  3      [ ]         STREAM     CONNECTED     13616    @/dbus-vfs-daemon/socket-IjLgcUuq
unix  3      [ ]         STREAM     CONNECTED     13608    
unix  3      [ ]         STREAM     CONNECTED     13600    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13599    
unix  3      [ ]         STREAM     CONNECTED     13597    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     13596    
unix  3      [ ]         STREAM     CONNECTED     13583    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     13582    
unix  3      [ ]         STREAM     CONNECTED     13576    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13575    
unix  3      [ ]         STREAM     CONNECTED     12672    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     12671    
unix  3      [ ]         STREAM     CONNECTED     12666    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     12665    
unix  3      [ ]         STREAM     CONNECTED     12663    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12662    
unix  3      [ ]         STREAM     CONNECTED     13571    /tmp/orbit-ba/linc-5ec-0-e2530f69cf7f
unix  3      [ ]         STREAM     CONNECTED     12606    
unix  3      [ ]         STREAM     CONNECTED     12605    /tmp/orbit-ba/linc-4f9-0-d667b0313e79
unix  3      [ ]         STREAM     CONNECTED     13569    
unix  3      [ ]         STREAM     CONNECTED     12597    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13560    
unix  3      [ ]         STREAM     CONNECTED     12595    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     13555    
unix  3      [ ]         STREAM     CONNECTED     13554    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12589    
unix  3      [ ]         STREAM     CONNECTED     13520    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     13519    
unix  3      [ ]         STREAM     CONNECTED     12565    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     13499    
unix  3      [ ]         STREAM     CONNECTED     13489    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12508    
unix  3      [ ]         STREAM     CONNECTED     12503    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     12502    
unix  3      [ ]         STREAM     CONNECTED     12500    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13483    
unix  3      [ ]         STREAM     CONNECTED     12499    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13481    
unix  3      [ ]         STREAM     CONNECTED     12393    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     13476    
unix  3      [ ]         STREAM     CONNECTED     11261    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     11260    
unix  3      [ ]         STREAM     CONNECTED     12175    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11257    
unix  3      [ ]         STREAM     CONNECTED     11256    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12173    
unix  3      [ ]         STREAM     CONNECTED     11222    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     12167    
unix  3      [ ]         STREAM     CONNECTED     12165    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     11221    
unix  3      [ ]         STREAM     CONNECTED     11211    @/tmp/.ICE-unix/1203
unix  3      [ ]         STREAM     CONNECTED     12156    
unix  3      [ ]         STREAM     CONNECTED     12140    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11198    
unix  3      [ ]         STREAM     CONNECTED     12107    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11184    
unix  3      [ ]         STREAM     CONNECTED     11183    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     12106    
unix  3      [ ]         STREAM     CONNECTED     12105    /tmp/orbit-ba/linc-579-0-1f5c0dc75434b
unix  3      [ ]         STREAM     CONNECTED     11182    
unix  3      [ ]         STREAM     CONNECTED     11181    /tmp/orbit-ba/linc-4f9-0-d667b0313e79
unix  3      [ ]         STREAM     CONNECTED     12103    
unix  3      [ ]         STREAM     CONNECTED     11175    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12095    
unix  3      [ ]         STREAM     CONNECTED     12091    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     11146    
unix  3      [ ]         STREAM     CONNECTED     11137    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     12090    
unix  3      [ ]         STREAM     CONNECTED     12089    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     11136    
unix  3      [ ]         STREAM     CONNECTED     12084    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     12083    
unix  3      [ ]         STREAM     CONNECTED     12070    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11131    
unix  3      [ ]         STREAM     CONNECTED     12065    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12064    
unix  3      [ ]         STREAM     CONNECTED     12063    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12062    
unix  3      [ ]         STREAM     CONNECTED     12059    @/dbus-vfs-daemon/socket-WkTRQwSw
unix  3      [ ]         STREAM     CONNECTED     12058    
unix  3      [ ]         STREAM     CONNECTED     12057    @/dbus-vfs-daemon/socket-GhOi2Jg2
unix  3      [ ]         STREAM     CONNECTED     12056    
unix  3      [ ]         STREAM     CONNECTED     12050    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     12049    
unix  3      [ ]         STREAM     CONNECTED     12046    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     12045    
unix  3      [ ]         STREAM     CONNECTED     12028    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     11104    
unix  3      [ ]         STREAM     CONNECTED     11103    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     12027    
unix  3      [ ]         STREAM     CONNECTED     11984    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     11067    
unix  3      [ ]         STREAM     CONNECTED     11977    /tmp/orbit-ba/linc-570-0-1a64d97bc1ea0
unix  3      [ ]         STREAM     CONNECTED     11976    
unix  3      [ ]         STREAM     CONNECTED     11058    /tmp/orbit-ba/linc-4f9-0-d667b0313e79
unix  3      [ ]         STREAM     CONNECTED     11974    
unix  3      [ ]         STREAM     CONNECTED     11014    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     11892    
unix  3      [ ]         STREAM     CONNECTED     11008    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     11888    
unix  3      [ ]         STREAM     CONNECTED     11883    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     11006    
unix  3      [ ]         STREAM     CONNECTED     11876    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10994    
unix  3      [ ]         STREAM     CONNECTED     11869    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11865    
unix  3      [ ]         STREAM     CONNECTED     11866    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     10989    
unix  3      [ ]         STREAM     CONNECTED     10980    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11857    
unix  3      [ ]         STREAM     CONNECTED     10978    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     10977    
unix  3      [ ]         STREAM     CONNECTED     11847    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     10974    
unix  3      [ ]         STREAM     CONNECTED     10973    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10972    
unix  3      [ ]         STREAM     CONNECTED     11844    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     11843    
unix  3      [ ]         STREAM     CONNECTED     11840    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     11839    
unix  3      [ ]         STREAM     CONNECTED     10943    /tmp/orbit-ba/linc-540-0-2b8e834ae4171
unix  3      [ ]         STREAM     CONNECTED     11838    
unix  3      [ ]         STREAM     CONNECTED     10937    
unix  3      [ ]         STREAM     CONNECTED     10936    
unix  3      [ ]         STREAM     CONNECTED     11821    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     11820    
unix  3      [ ]         STREAM     CONNECTED     11800    /tmp/orbit-ba/linc-4f9-0-d667b0313e79
unix  3      [ ]         STREAM     CONNECTED     11799    
unix  3      [ ]         STREAM     CONNECTED     10865    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10863    
unix  3      [ ]         STREAM     CONNECTED     10857    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10856    
unix  3      [ ]         STREAM     CONNECTED     11726    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     11725    
unix  3      [ ]         STREAM     CONNECTED     11724    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     11723    
unix  3      [ ]         STREAM     CONNECTED     11722    /tmp/orbit-ba/linc-53a-0-14a24566bf631
unix  3      [ ]         STREAM     CONNECTED     11721    
unix  3      [ ]         STREAM     CONNECTED     11719    /tmp/orbit-ba/linc-4f9-0-d667b0313e79
unix  3      [ ]         STREAM     CONNECTED     11718    
unix  3      [ ]         STREAM     CONNECTED     11717    /home/ba/.pulse/ceca739e94a5ded55a826c900000000b-runtime/native
unix  3      [ ]         STREAM     CONNECTED     10854    
unix  3      [ ]         STREAM     CONNECTED     11716    /tmp/orbit-ba/linc-537-0-331d8d55bd005
unix  3      [ ]         STREAM     CONNECTED     11715    
unix  3      [ ]         STREAM     CONNECTED     10847    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     11712    
unix  3      [ ]         STREAM     CONNECTED     10846    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     11711    
unix  3      [ ]         STREAM     CONNECTED     10841    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11704    
unix  3      [ ]         STREAM     CONNECTED     11644    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11643    
unix  3      [ ]         STREAM     CONNECTED     11645    /tmp/orbit-ba/linc-4f9-0-d667b0313e79
unix  3      [ ]         STREAM     CONNECTED     10794    
unix  3      [ ]         STREAM     CONNECTED     10788    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     11642    
unix  3      [ ]         STREAM     CONNECTED     11598    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10775    
unix  3      [ ]         STREAM     CONNECTED     11587    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     10763    
unix  2      [ ]         DGRAM                    10761    
unix  3      [ ]         STREAM     CONNECTED     11586    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     11585    
unix  2      [ ]         DGRAM                    11575    
unix  3      [ ]         STREAM     CONNECTED     10740    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10739    
unix  3      [ ]         STREAM     CONNECTED     11571    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     11570    
unix  3      [ ]         STREAM     CONNECTED     10738    /tmp/orbit-ba/linc-526-0-3819355410654
unix  3      [ ]         STREAM     CONNECTED     11569    
unix  3      [ ]         STREAM     CONNECTED     10736    /tmp/orbit-ba/linc-520-0-3d53d261f06c0
unix  3      [ ]         STREAM     CONNECTED     11568    
unix  3      [ ]         STREAM     CONNECTED     11567    /tmp/orbit-ba/linc-4f9-0-d667b0313e79
unix  3      [ ]         STREAM     CONNECTED     10735    
unix  3      [ ]         STREAM     CONNECTED     11558    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     11557    
unix  3      [ ]         STREAM     CONNECTED     10716    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     11556    
unix  3      [ ]         STREAM     CONNECTED     10713    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11555    
unix  3      [ ]         STREAM     CONNECTED     10712    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     10711    
unix  3      [ ]         STREAM     CONNECTED     11554    /tmp/orbit-ba/linc-4f9-0-d667b0313e79
unix  3      [ ]         STREAM     CONNECTED     10710    
unix  3      [ ]         STREAM     CONNECTED     10706    /tmp/orbit-ba/linc-524-0-501124976256
unix  3      [ ]         STREAM     CONNECTED     11550    
unix  3      [ ]         STREAM     CONNECTED     11549    /tmp/orbit-ba/linc-4f9-0-d667b0313e79
unix  3      [ ]         STREAM     CONNECTED     10704    
unix  3      [ ]         STREAM     CONNECTED     10693    /tmp/orbit-ba/linc-51e-0-13b8262d6e069
unix  3      [ ]         STREAM     CONNECTED     10692    
unix  3      [ ]         STREAM     CONNECTED     10690    /tmp/orbit-ba/linc-4f9-0-d667b0313e79
unix  3      [ ]         STREAM     CONNECTED     10689    
unix  3      [ ]         STREAM     CONNECTED     10684    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     11548    
unix  3      [ ]         STREAM     CONNECTED     10682    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11545    
unix  3      [ ]         STREAM     CONNECTED     10681    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11544    
unix  3      [ ]         STREAM     CONNECTED     11540    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10677    
unix  3      [ ]         STREAM     CONNECTED     10673    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11539    
unix  3      [ ]         STREAM     CONNECTED     10665    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     11536    
unix  3      [ ]         STREAM     CONNECTED     10632    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11504    
unix  3      [ ]         STREAM     CONNECTED     10630    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10629    
unix  3      [ ]         STREAM     CONNECTED     10588    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     11439    
unix  3      [ ]         STREAM     CONNECTED     11408    @/tmp/.ICE-unix/1203
unix  3      [ ]         STREAM     CONNECTED     10558    
unix  3      [ ]         STREAM     CONNECTED     11407    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10556    
unix  3      [ ]         STREAM     CONNECTED     10552    @/tmp/.ICE-unix/1203
unix  3      [ ]         STREAM     CONNECTED     11379    
unix  3      [ ]         STREAM     CONNECTED     10551    /tmp/orbit-ba/linc-50f-0-35d5434335472
unix  3      [ ]         STREAM     CONNECTED     11378    
unix  3      [ ]         STREAM     CONNECTED     11377    /tmp/orbit-ba/linc-4f9-0-d667b0313e79
unix  3      [ ]         STREAM     CONNECTED     10549    
unix  3      [ ]         STREAM     CONNECTED     11370    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     10537    
unix  3      [ ]         STREAM     CONNECTED     10533    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     11369    
unix  3      [ ]         STREAM     CONNECTED     10513    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11355    
unix  2      [ ]         DGRAM                    11354    
unix  3      [ ]         STREAM     CONNECTED     10507    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11347    
unix  3      [ ]         STREAM     CONNECTED     10506    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10505    
unix  3      [ ]         STREAM     CONNECTED     10454    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     11310    
unix  3      [ ]         STREAM     CONNECTED     10450    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     11308    
unix  3      [ ]         STREAM     CONNECTED     10443    /tmp/orbit-ba/linc-502-0-58e0d2a077286
unix  3      [ ]         STREAM     CONNECTED     10442    
unix  3      [ ]         STREAM     CONNECTED     10440    /tmp/orbit-ba/linc-4f9-0-d667b0313e79
unix  3      [ ]         STREAM     CONNECTED     11299    
unix  3      [ ]         STREAM     CONNECTED     10430    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     11288    
unix  3      [ ]         STREAM     CONNECTED     11287    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     10422    
unix  3      [ ]         STREAM     CONNECTED     10420    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11285    
unix  3      [ ]         STREAM     CONNECTED     9169     @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     9168     
unix  3      [ ]         STREAM     CONNECTED     9162     /tmp/orbit-ba/linc-4b3-0-41ce48db5272f
unix  3      [ ]         STREAM     CONNECTED     10305    
unix  3      [ ]         STREAM     CONNECTED     10304    /tmp/orbit-ba/linc-4f9-0-d667b0313e79
unix  3      [ ]         STREAM     CONNECTED     9160     
unix  3      [ ]         STREAM     CONNECTED     10302    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9156     
unix  3      [ ]         STREAM     CONNECTED     9085     @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     10203    
unix  3      [ ]         STREAM     CONNECTED     10155    @/tmp/dbus-sDUiMlXeuG
unix  3      [ ]         STREAM     CONNECTED     9050     
unix  3      [ ]         STREAM     CONNECTED     10151    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9048     
unix  3      [ ]         STREAM     CONNECTED     9045     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9044     
unix  3      [ ]         STREAM     CONNECTED     10150    
unix  3      [ ]         STREAM     CONNECTED     10149    
unix  3      [ ]         STREAM     CONNECTED     9042     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10139    
unix  3      [ ]         STREAM     CONNECTED     8936     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10079    
unix  2      [ ]         DGRAM                    8933     
unix  3      [ ]         STREAM     CONNECTED     8932     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10074    
unix  3      [ ]         STREAM     CONNECTED     8931     @/tmp/gdm-session-scCtdyaV
unix  3      [ ]         STREAM     CONNECTED     10070    
unix  3      [ ]         STREAM     CONNECTED     8928     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10068    
unix  3      [ ]         STREAM     CONNECTED     10025    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     8874     
unix  3      [ ]         STREAM     CONNECTED     9388     /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     8477     
unix  3      [ ]         STREAM     CONNECTED     8396     
unix  3      [ ]         STREAM     CONNECTED     8395     
unix  2      [ ]         DGRAM                    8369     
unix  3      [ ]         STREAM     CONNECTED     8367     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8366     
unix  3      [ ]         STREAM     CONNECTED     8300     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9261     
unix  3      [ ]         STREAM     CONNECTED     9233     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8298     
unix  3      [ ]         STREAM     CONNECTED     8289     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8288     
unix  2      [ ]         DGRAM                    8120     
unix  2      [ ]         DGRAM                    8119     
unix  3      [ ]         STREAM     CONNECTED     6906     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7984     
unix  2      [ ]         DGRAM                    7983     
unix  3      [ ]         STREAM     CONNECTED     7726     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7725     
unix  3      [ ]         STREAM     CONNECTED     7706     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7705     
unix  2      [ ]         DGRAM                    7696     
unix  3      [ ]         STREAM     CONNECTED     7675     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7674     
unix  3      [ ]         STREAM     CONNECTED     7666     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     6784     
unix  2      [ ]         DGRAM                    6763     
unix  3      [ ]         STREAM     CONNECTED     6750     @/com/ubuntu/upstart
unix  3      [ ]         STREAM     CONNECTED     6748     
unix  3      [ ]         STREAM     CONNECTED     7613     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     6697     
unix  3      [ ]         STREAM     CONNECTED     6692     
unix  3      [ ]         STREAM     CONNECTED     6691     
unix  2      [ ]         DGRAM                    6688     
unix  3      [ ]         STREAM     CONNECTED     7603     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7602     
unix  3      [ ]         STREAM     CONNECTED     6654     
unix  3      [ ]         STREAM     CONNECTED     6653     
unix  3      [ ]         DGRAM                    7382     
unix  3      [ ]         DGRAM                    7381     
unix  3      [ ]         STREAM     CONNECTED     7337     @/com/ubuntu/upstart
unix  3      [ ]         STREAM     CONNECTED     7334     
```Also do you have ssh keys? [COLOR=Blue]**I believe so.**[/COLOR] Are they in the right place?  i.e. ~/.ssh 
I could cd into ```
~/.ssh
```, but ```
ls
``` returned nothing.

---

### Post by strask on 2012-04-17
Just a quick sanity check... you said you tried this:
```
telnet xx.xx.xxx.xxx 22xx
```What are the last two 'x' characters for? It seems like you are running ssh on a port other than 22, which could explain your connection troubles. Assuming you are running it on port 2299, the correct command line would be similar to this:
```
ssh user@xx.xx.xxx.xxx:2299
```Because ssh assumes port 22 unless you tell it otherwise.

---

### Post by itba on 2012-04-17
I re-ran it as follows:
```
ssh user@xx.xx.xxx.xxx :2204
```

and it gives the following error:
```
ssh: connect to host xx.xx.xxx.xxx port 22: Connection timed out

```

---

### Post by strask on 2012-04-17
Don't put a space between the ip address and the :

---

### Post by itba on 2012-04-17
well, then I get the following error:
ssh: Could not resolve hostname xx.xx.xxx.xxx:: Name or service not known

---

### Post by strask on 2012-04-18
My deepest apologies I was using antiquated syntax. Try ```
ssh -p 2204 user@xx.xx.xxx.xxx
```

---

### Post by itba on 2012-04-18
no worries, strask....that did work - thanks!
 - so, what does the -p indicate...
this is what it returned:
```
The authenticity of host '[xx.xx.xxx.xxx]:2204 ([xx.xx.xxx.xxx]:2204)' can't be established.
RSA key fingerprint is xx:cx:xe:xx:ax:xx:xx:xx:d0:7b:ae:bd:xx:fx:xx:xx.
Are you sure you want to continue connecting (yes/no)? y
Please type 'yes' or 'no': yes
Warning: Permanently added '[xx.xx.xxx.xxx]:2204' (RSA) to the list of known hosts.
user@xx.xx.xxx.xxx's password: 
Permission denied, please try again.
```of course now I have to figure out why it is not accepting the password
I figured out the password problem, so it works

---

### Post by strask on 2012-04-18
> **itba said:**
> so, what does the -p indicate...

-p indicates that you are specifying a non-default port number; the 2204 or whatever needs to be the next thing on the command line after the -p.

> I figured out the password problem, so it works

Congratulations!

---

### Post by mikaelcrocker on 2012-04-18
> **itba said:**
> well, then I get the following error:
ssh: Could not resolve hostname xx.xx.xxx.xxx:: Name or service not known

Going back to what I was saying concerning ~/.ssh  So you're trying to just ssh in there with no password?  You'll need to do an ssh key-gen -t rsa (the syntax is close to that)  However while I do think this needs to be done is ssh installed on both machines.

It's just odd you're not getting permissions issues, looks like a syntax error on your hostname.  Is this an internal IP external, port forwarding on a router perhaps?

---

### Post by strask on 2012-04-18
> **mikaelcrocker said:**
> It's just odd you're not getting permissions issues, looks like a syntax error on your hostname.  Is this an internal IP external, port forwarding on a router perhaps?

That was *my* fault. 

I told him to use ```
ssh user@host:port
``` which is wrong.
Correct way is ```
ssh -p port user@host
```.

He is connecting now, and password authentication works per his most recent edit. I'm sure the next questions will be about setting up keys and stuff, of course.

---

### Post by itba on 2012-04-18
thanks strask....you guessed right - how do I go about setting up the key so that I don't have to enter the password

---

### Post by strask on 2012-04-18
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys) has a nice writeup on the basics of how public-key authentication works.

If you want to be able to log in without using a password at all, you can choose to leave the password empty (just press enter) when prompted by ssh-keygen.

The better way is to go ahead and set the password when prompted, then use the ssh-agent program and ssh-add command to set things up so you only have to type your password once per login session. That can get complicated, but once it's working the way you want it is really nice.

---

### Post by itba on 2012-04-19
sounds good strask. hopefully I can do it seamlessly. will update this post.

---

### Post by itba on 2012-05-15
how do I copy files from the remote host to my hard drive and from my hard drive to the remote machine.
I logged into the remote machine and tried 
cp xyz.cpp ~/home/ba

but it was looking for /home/ba/ in the directory of the remote machine.

---

### Post by mikaelcrocker on 2012-05-15
When you have   ~/    that is home by default, so you're saying ~/home/ba is really home/ba/home/ba.

Also when copying files across servers, use scp oppose to cp it's more secure.  You need to specify the host.. so scp xyz.cpp [email]user@remoteserver.com[/email]:~/

---

### Post by itba on 2012-05-15
> **mikaelcrocker said:**
> When you have   ~/    that is home by default, so you're saying ~/home/ba is really home/ba/home/ba.

Also when copying files across servers, use scp oppose to cp it's more secure.  You need to specify the host.. so scp xyz.cpp [EMAIL="user@remoteserver.com"]user@remoteserver.com[/EMAIL]:~/

@mikaelcrocker, thanks, that worked, except it copied in the home of the remote server (test) and not my hard drive.
I ran the following code:
```
[test@ga ~]$ scp -P 22xx /home/ts/src/stock.cpp test@xx.xx.xxx.231:~/
```and while on the remote server, I did the following:
```
[test@ga ~]$ ls
src  stock.cpp
```obviously I am doing it wrong. 
so I tried the following:
```
[test@ga ~]$ scp /home/ts/src/stock.cpp ba@192.168.1.1:~/
```where ba is the name of my computer
but at this point it just hangs and times out
EDIT: I had the wrong IP for my computer so I corrected it, and it asks me for the password. I just used my regular password, since it is my personal computer, and I get the following message:
```
Permission denied (publickey,gssapi-keyex,gssapi-with-mic,password).
lost connection
```
where do I get/reset the password at for this purpose.

---

### Post by strask on 2012-05-16
Hi again itba. :)

Ok it looks like you got the syntax right in your last post, but just to confirm... assuming you have a computer on your desktop named 'desktop', and the test system is named 'testsystem'. If you want to copy a file from your desktop to your test system you can do either this```
user@desktop ~]$ scp -p 22xx localfile.txt user@testsystem:/path/to/destination/
```
Or you could do the same thing from the test system by typing```
user@testsystem ~]$ scp user@desktop:localfile.txt /path/to/destination/
```

To copy a file from the test system to your desktop, you just reverse either of the two commands like this: ```
user@desktop ~]$ scp -p 22xx user@testsystem:/path/to/remotefile.txt .
```or```
user@testsystem ~]$ scp /path/to/remotefile.txt user@desktop:~/
```

Ok, so I'm thinking that you have ssh set up fine to go from your desktop to the test system, but the reverse isn't working so well. You could just issue all of your ssh and scp commands on the desktop, with the test system as the destination, or you could fix your problem that is preventing you from going from the test system back to your desktop. To shed some more light on what that problem might be, log into the test system then try to ssh back to your desktop with the -vv option to make ssh give us lots of debugging output. ```
user@testsystem ~]$ ssh -vv user@desktop
```

---

### Post by itba on 2012-05-30
> **strask said:**
> Hi again itba. :)

Ok it looks like you got the syntax right in your last post, but just to confirm... assuming you have a computer on your desktop named 'desktop', and the test system is named 'testsystem'. If you want to copy a file from your desktop to your test system you can do either this```
user@desktop ~]$ scp -p 22xx localfile.txt user@testsystem:/path/to/destination/
```Or you could do the same thing from the test system by typing```
user@testsystem ~]$ scp user@desktop:localfile.txt /path/to/destination/
```To copy a file from the test system to your desktop, you just reverse either of the two commands like this: ```
user@desktop ~]$ scp -p 22xx user@testsystem:/path/to/remotefile.txt .
```or```
user@testsystem ~]$ scp /path/to/remotefile.txt user@desktop:~/
```Ok, so I'm thinking that you have ssh set up fine to go from your desktop to the test system, but the reverse isn't working so well. You could just issue all of your ssh and scp commands on the desktop, with the test system as the destination, or you could fix your problem that is preventing you from going from the test system back to your desktop. To shed some more light on what that problem might be, log into the test system then try to ssh back to your desktop with the -vv option to make ssh give us lots of debugging output. ```
user@testsystem ~]$ ssh -vv user@desktop
```

hi strask,
thanks again, that worked. I am able to copy back and forth now.
now, I am trying to open port 9999 on my computer for incoming                 connections on my firewall and listen on that port. 
I ran ```
netstat -nl|grep 99
``` and it doesn't show 9999.
how do I open the port (I have a dynamic IP)

---

### Post by strask on 2012-05-30
> **itba said:**
> now, I am trying to open port 9999 on my computer for incoming                 connections on my firewall and listen on that port.

I think I need you to use more words. :) But I'll assume the following:

[LIST=1]
[*]You want sshd to listen on port 9999 (that is, you aren't talking about some other program now)
[*]You are talking about the local firewall on your ubuntu system, not a separate firewall device.
[/LIST]
 > I ran ```
netstat -nl|grep 99
``` and it doesn't show 9999.
how do I open the port (I have a dynamic IP)

I think you are confusing a couple of issues here. The netstat command will show you ports that are being listened to by server processes on your system. It doesn't show you anything about what ports are open on your firewall. So you may well have configured the firewall to allow port 9999, but netstat won't show you that.

Since netstat isn't showing a listening process on port 9999, that means that either sshd isn't running, or it's configured to listen on some other port. First try ```
ps -ef |grep sshd
```
If it's not running, start it: ```
sudo service ssh start
```

If it is running, it must be running on the wrong port. Edit /etc/ssh/sshd_config and adjust the line that starts with "Port" to say "Port 9999".

Once it is running and on the correct port, your netstat command should reflect this. Then you just need to deal with the firewall settings. Good starting points for this are listed in a sticky on the security section of the forums ([http://ubuntuforums.org/showthread.php?t=1871177](http://ubuntuforums.org/showthread.php?t=1871177)) but if you have specific questions feel free to ask.

---

### Post by itba on 2012-05-31
> **strask said:**
> I think I need you to use more words. :) But I'll assume the following:

[LIST=1]
[*]You want sshd to listen on port 9999 (that is, you aren't talking about some other program now)
[*]You are talking about the local firewall on your ubuntu system, not a separate firewall device.
[/LIST]
 

I think you are confusing a couple of issues here. The netstat command will show you ports that are being listened to by server processes on your system. It doesn't show you anything about what ports are open on your firewall. So you may well have configured the firewall to allow port 9999, but netstat won't show you that.

Since netstat isn't showing a listening process on port 9999, that means that either sshd isn't running, or it's configured to listen on some other port. First try ```
ps -ef |grep sshd
```If it's not running, start it: ```
sudo service ssh start
```If it is running, it must be running on the wrong port. Edit /etc/ssh/sshd_config and adjust the line that starts with "Port" to say "Port 9999".

Once it is running and on the correct port, your netstat command should reflect this. Then you just need to deal with the firewall settings. Good starting points for this are listed in a sticky on the security section of the forums ([http://ubuntuforums.org/showthread.php?t=1871177](http://ubuntuforums.org/showthread.php?t=1871177)) but if you have specific questions feel free to ask.

hi strask,
yes I think I should have been more specific, and I perhaps should have started a new thread.
the issue I am facing is - I need to open port 9999 to listen to a data feed from another server on another network. I ssh into that computer(let's call it X) and try to run the program to  listen to the data feed, but I get a "Bad file descriptor" message.
So, I tried the following:

```
sudo iptables -A INPUT -i eth0 -p tcp --sport 99 -j ACCEPT
```but that did not work. it gave me the same error message.

so, I ran (where 68.193.xx.xxx is the ipaddress of my computer)
```
nmap -v -A 68.193.xx.xxx
```and it indicated that port 5678 was open.

So, I ssh into X and try the following:
```
telnet 68.193.xx.xxx 5678
```but I get the below:
```

Trying 68.193.xx.xxx...
telnet: connect to address 68.193.xx.xxx: Connection timed out
```I read your message above and I think I better understand what netstat is doing. It seems like I shouldn't need it for what I am trying to achieve, regardless, I ran the following
```
ps -ef | grep sshd
root       733     1  0 11:21 ?        00:00:00 /usr/sbin/sshd -D
ba     3076  2550  0 13:59 pts/1    00:00:00 grep --color=auto sshd
```then I ran:
 ```
sudo service ssh start
```and it gave the following result
```
start: Job is already running: ssh
```I tried to open the sshd_config, but that file doesn't exist. 


I am perplexed as to why when 5678 is open it shouldn't work, and secondly when I ran the iptables command above, that it did not open port 99. 
How do I get this to work so I can listen to the data feed (I have DHCP).

---

### Post by strask on 2012-05-31
> **itba said:**
> and I perhaps should have started a new thread.
Perhaps... If I am reading your message correctly, it seems ssh is working fine and this is no longer an ssh issue at all, right?

> the issue I am facing is - I need to open port 9999 to listen to a data feed from another server on another network. I ssh into that computer(let's call it X) and try to run the program to  listen to the data feed, but I get a "Bad file descriptor" message.

Ok so I think you are saying that X is the local server that is listening (on port 9999) to a data feed from server Y on a remote network, yes?

What program is doing the listening? That is, which program gives you the bad file descriptor message? This message usually results from a c programming error, as far as I know.... I don't think it's a firewall issue.

> So, I tried the following:

```
sudo iptables -A INPUT -i eth0 -p tcp --sport 99 -j ACCEPT
```but that did not work. it gave me the same error message.

so, I ran 
```
nmap -v -A 68.193.xx.xxx
```and it indicated that port 5678 was open.

So, I ssh into X and try the following:
```
telnet 68.193.xx.xxx 5678
```but I get the below:
```

Trying 68.193.xx.xxx...
telnet: connect to address 68.193.xx.xxx: Connection timed out
```

I assume that 68.193.xx.xxx is server Y, from which the data feed originates? If so, why are you trying to initiate a connection INTO that machine? I thought you were listening for connections FROM server Y?

> and secondly when I ran the iptables command above, that it did not open port 99.

That part is pretty simple, if I'm reading you correctly. You specified a source port of 99, when you should have specified it as a destination port.
 
> How do I get this to work so I can listen to the data feed (I have DHCP).

I'm going to brainstorm this a little bit, starting from the top. I'm assuming that server X is your local server that RECEIVES the connections, and that server Y is the remote server that INITIATES the connections.

First thing to do is log into server X and run the program that listens for the incoming connection. If that's giving you bad file descriptor messages, then you have a problem unrelated to networking and need to fix it before you can continue -- obviously if you can't get the program to listen, the rest is irrelevant.

Second thing, once that program is running, is to think about your network configuration... is server X behind a NATing router or firewall? If so the router/firewall needs to be configured to forward port 9999 connections to server X -- how to do this depends on the brand/type of router.

Third thing is to test the connection by having server Y attempt to feed some data. If it works, you are done. If it fails to work, because of a connection time out or connection refused, you may need to revisit your iptables configuration.

---

### Post by itba on 2012-05-31
> **strask said:**
> Perhaps... If I am reading your message correctly, it seems ssh is working fine and this is no longer an ssh issue at all, right?
[COLOR=Blue]Yes indeed, ssh is working fine :-)[/COLOR]


Ok so I think you are saying that X is the local server that is listening (on port 9999) to a data feed from server Y on a remote network, yes?
[COLOR=Blue]Yes [/COLOR]

What program is doing the listening? [COLOR=Blue]C++ [/COLOR]That is, which program gives you the bad file descriptor message? This message usually results from a c programming error, as far as I know.... I don't think it's a firewall issue.



I assume that 68.193.xx.xxx is server Y, from which the data feed originates? [COLOR=Blue](this is the IP of X, i.e. my computer) [/COLOR]If so, why are you trying to initiate a connection INTO that machine? I thought you were listening for connections FROM server Y? [COLOR=Blue]Yes, I am listening for connections from Y.[/COLOR][COLOR=Blue]
[/COLOR] 


That part is pretty simple, if I'm reading you correctly. You specified a source port of 99, when you should have specified it as a destination port. [COLOR=Blue]oh I see...so, should I run the same command with --dport instead of --sport[/COLOR]
 


I'm going to brainstorm this a little bit, starting from the top. I'm assuming that server X is your local server that RECEIVES the connections, and that server Y is the remote server that INITIATES the connections. [COLOR=Blue]absolutely.[/COLOR]

First thing to do is log into server X and run the program that listens for the incoming connection. [COLOR=Blue]the program is housed on server Y, and when I run it from there I still get the bad file descriptor message, so now i wonder if that is a program issue as you mentioned. [/COLOR]If that's giving you bad file descriptor messages, then you have a problem unrelated to networking and need to fix it before you can continue -- obviously if you can't get the program to listen, the rest is irrelevant. 

Second thing, once that program is running, is to think about your network configuration... is server X behind a NATing router or firewall? [COLOR=Blue]how do I figure that out. [/COLOR]If so the router/firewall needs to be configured to forward port 9999 connections to server X -- how to do this depends on the brand/type of router. [COLOR=Blue]i have a motorola SBV5120 modem and a Linksys BEFW11S4 V4 router. [/COLOR]

Third thing is to test the connection by having server Y attempt to feed some data. If it works, you are done. If it fails to work, because of a connection time out or connection refused, you may need to revisit your iptables configuration.
   [COLOR=Blue]So I telnet from Y to the IP and port on my machine (i.e. X) and  I get the following :
[/COLOR]```
telnet 68.193.xx.xxx 5678
Trying 68.193.xx.xxx...
telnet: connect to address 68.193.xx.xxx: Connection timed out
```[COLOR=Blue]
How do I fix my iptables configuration in this case?

I also ran the following from my machine X:
On one shell I ran ```
nc -l 5678
``` and on another shell, the following:

[/COLOR]```
telnet 192.168.15.2  5678//[COLOR=Blue]this is my NIC...[/COLOR]
Trying 192.168.15.2...
Connected to 192.168.15.2.
Escape character is '^]'.
^]

and this is my public IP (so does that mean I am behind a NAT'ing router)
telnet 68.193.xx.xxx 5678
Trying 68.193.xx.xxx...
Connected to 68.193.xx.xxx.
Escape character is '^]'.
Connection closed by foreign host.

```[COLOR=Blue]
[/COLOR]

---

### Post by itba on 2012-05-31
hi strask,
I think there is a problem with my firewall on my ubuntu box.
I tried to ping from a windows box on the LAN into my ubuntu box and I get a Request timed out.
however, it works from ubuntu to windows.
I ran
sudo ufw disable
and restarted my machines and also went into firestarter and looked if the firewall was disabled and it confirmed it.
I can ping from my windows and linux box into my router also, so I am guessing it is not a router issue.
any thoughts on how to fix this. why won't the windows machine ping the ubuntu machine :confused:

---

### Post by strask on 2012-06-01
> **itba said:**
> [COLOR=Blue][COLOR=Black]the  program is housed on server Y, and when I run it from there I still get  the bad file descriptor message, so now i wonder if that is a program  issue as you mentioned.[/COLOR][/COLOR][COLOR=Blue][COLOR=Black]

Wait a minute, I am unfortunately confused again. 

In order to make a network connection from Y to X, you need two programs. One, running on Y, initiates the network connection and the other, running on X, listens for the inbound connection.

In your case, what are these two programs? So far all you mentioned was C++; that's a programming language but not an actual program.

Are you getting bad file descriptor errors from both programs? Did you write the programs yourself? If not, where did you get them from?

[/COLOR][/COLOR]> [QUOTE]is server X behind a NATing router or firewall?[COLOR=Black]how do I figure that out
... 
[/COLOR][COLOR=Black]i have a motorola SBV5120 modem and a Linksys BEFW11S4 V4 router. 

telnet 192.168.15.2  5678  // [/COLOR][COLOR=Black]this is my NIC...
...
and this is my public IP (so does that mean I am behind a NAT'ing router)[/COLOR] [COLOR=Black]
t[/COLOR]elnet 68.193.xx.xxx 5678[COLOR=Blue]
[/COLOR][/QUOTE]Yes, that means you are behind a NATing router (the Linksys). NAT stands for Network Address Translation, it's what converts your private ip address on the 192 network to a public net 68 address.

When you are making an outbound connection, the packets leave your computer with a "return address" of 192.168.15.2; that address is no good on the public internet. So the router re-writes the return address to your public IP address of 68.193.xx.xxx, so that the website or whatever other computer you connect to knows how to reach back to you. When the response arrives at your router, it has a destination address of 68.193.xx.xxx, which your computer knows nothing about. So it adjusts the destination address to 192.168.15.2, before forwarding the packets onto your local network.

 The problem arises when you want to accept unsolicited connections from the internet; the remote host has to use your public address of 68.193.xx.xxx, but your router doesn't know which machine on your local network should receive the connection. So by default it just drops it. You need to go into your linksys configuration and tell it to forward all requests with a destination port number of 9999 to 192.168.15.2.

---

### Post by rajivweb on 2012-06-01
Use netstat command to overcome from this problem.

---

### Post by itba on 2012-06-01
> **strask said:**
> [COLOR=Blue][COLOR=Black]

Wait a minute, I am unfortunately confused again. 

In order to make a network connection from Y to X, you need two programs. One, running on Y, initiates the network connection and the other, running on X, listens for the inbound connection.

In your case, what are these two programs? So far all you mentioned was C++; that's a programming language but not an actual program.

Are you getting bad file descriptor errors from both programs? Did you write the programs yourself? If not, where did you get them from?

[/COLOR][/COLOR]Yes, that means you are behind a NATing router (the Linksys). NAT stands for Network Address Translation, it's what converts your private ip address on the 192 network to a public net 68 address.

When you are making an outbound connection, the packets leave your computer with a "return address" of 192.168.15.2; that address is no good on the public internet. So the router re-writes the return address to your public IP address of 68.193.xx.xxx, so that the website or whatever other computer you connect to knows how to reach back to you. When the response arrives at your router, it has a destination address of 68.193.xx.xxx, which your computer knows nothing about. So it adjusts the destination address to 192.168.15.2, before forwarding the packets onto your local network.

 The problem arises when you want to accept unsolicited connections from the internet; the remote host has to use your public address of 68.193.xx.xxx, but your router doesn't know which machine on your local network should receive the connection. So by default it just drops it. You need to go into your linksys configuration and tell it to forward all requests with a destination port number of 9999 to 192.168.15.2.

thanks again, strask. that's a great explanation.
can you tell me how I go about making the change on my linksys configuration. I opened the router page and I see the advanced routing tab where NAT is enabled. where do I make the change.

hi strask, also another point. I tried to ping my ubuntu box (say X1) from my windows box(say X2) on my LAN and I get a "request timed out". however, I can ping the windows box from ubuntu box??  I did this to see if there was a firewall issue on the ubuntu box that was preventing Y from talking to X. The assumption was that if there was no firewall issue on my ubuntu machine then my windows box on my LAN could ping the ubuntu box.
When I couldn't ping X1 from X2, I ran the following on X1
```
 sudo ufw disable
```and tried to ping X1 from X2 again, but with no luck :-(
does that mean that in addition to making the change on linksys, some change needs to be made on the ubuntu box to disable its firewall....

X1 not talking to X2 got resolved. X2 was on wireless and X1 on wired connection, and so X1 had an IP of 192.168.15.x, whereas X2 had an IP of 192.168.1.x. On the router I could forward the port only to 192.168.1.x, so that is what highlighted the problem. Now, I have both X1 and X2 on wired connection and X2 can ping X1, but the telnet from Y to X1 still doesn't work.
Firstly, I don't understand why with one being on wired and the other wireless on the same network that the Default gateway was different. The issue is resolved but if I can understand, that will help.
Secondly, now why is Y or for that matter even X2 not being able to telnet to X1.

---

### Post by strask on 2012-06-01
> **itba said:**
> can you tell me how I go about making the change on my linksys configuration. I opened the router page and I see the advanced routing tab where NAT is enabled. where do I make the change.
Unfortunately, I'm not able to help you with that part... you need to read the documentation for your router and if no luck there, maybe try posting a new thread about it for some fresh eyes.

> Firstly, I don't understand why with one being on wired and the other wireless on the same network that the Default gateway was different. The issue is resolved but if I can understand, that will help.Well, to me it looked like the router was creating two separate networks, 192.168.15 and 192.168.1; maybe it was keeping them separate for security reasons? I really don't know... that's most likely another linksys configuration question.

---

### Post by itba on 2012-06-02
> **strask said:**
> Unfortunately, I'm not able to help you with that part... you need to read the documentation for your router and if no luck there, maybe try posting a new thread about it for some fresh eyes.

Well, to me it looked like the router was creating two separate networks, 192.168.15 and 192.168.1; maybe it was keeping them separate for security reasons? I really don't know... that's most likely another linksys configuration question.

hi strask,
found some documentation about it and fixed it under Port forwarding in the Applications & Gaming section.
no worries, I am glad the problem is solved. 
Thanks for all your help along the way :p

---

### Post by eazyigz on 2013-01-09
> **strask said:**
> My deepest apologies I was using antiquated syntax. Try ```
ssh -p 2204 user@xx.xx.xxx.xxx
```
Yes, this works perfectly when all else fails.  Thanks!

---

