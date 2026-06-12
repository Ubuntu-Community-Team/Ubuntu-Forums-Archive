---
title: "Cannot install Skype on ubuntu and many packages missing from software center"
date: 2016-04-24
forum: Installation &amp; Upgrades
---

### Post by chewyboy000 on 2016-04-24
Whenever I try to install skype or steam from the software center  they are not there. I went to the terminal to install skype and I get  this:
 ```
 Reading package lists... Done Building dependency tree
Reading state information... Done Some packages could not be installed. This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming. The following information may help to resolve the situation:
  The following packages have unmet dependencies:  skype : Depends: skype-bin E: Unable to correct problems, you have held broken packages.
```
  The problem with this is that I don't have any broken packages  because I've checked many times. When I try to install skype with  aptitude it gives me the solution of deleting MANY system packages. This  is what it comes up with:
  ```
The following packages have unmet dependencies:  libllvm3.8 : Breaks: libllvm3.8:i386 (!= 1:3.8-2ubuntu3) but  1:3.8-2ubuntu1 is to be installed.  libllvm3.8:i386 : Breaks: libllvm3.8 (!= 1:3.8-2ubuntu1) but  1:3.8-2ubuntu3 is installed. open: 24; closed: 423; defer: 11; conflict: 28                                  .The following actions will resolve these dependencies:
    Remove the following packages:                                            
  1)      a11y-profile-manager-indicator
2)      account-plugin-facebook
3)      account-plugin-flickr
4)      account-plugin-google
5)      activity-log-manager
6)      adwaita-icon-theme
7)      aisleriot
8)      appmenu-qt5
9)      apport-gtk
10)     apturl
11)     arc-theme
12)     bamfdaemon
13)     baobab
14)     checkbox-converged
15)     checkbox-gui
16)     cheese
17)     compiz
18)     compiz-gnome
19)     compiz-plugins-default
20)     deja-dup
21)     dosbox
22)     eog
23)     evince
24)     evolution-data-server
25)     file-roller
26)     fwupd
27)     gcr
28)     gdebi
29)     gedit
30)     gir1.2-appindicator3-0.1
31)     gir1.2-gtk-3.0
32)     gir1.2-gtksource-3.0
33)     gir1.2-peas-1.0
34)     gir1.2-rb-3.0
35)     gir1.2-totem-1.0
36)     gir1.2-totem-plparser-1.0
37)     gir1.2-vte-2.91
38)     gir1.2-webkit2-4.0
39)     gir1.2-wnck-3.0
40)     gkbd-capplet
41)     gnome-bluetooth
42)     gnome-calculator
43)     gnome-calendar
44)     gnome-disk-utility
45)     gnome-font-viewer
46)     gnome-icon-theme
47)     gnome-keyring
48)     gnome-mahjongg
49)     gnome-mines
50)     gnome-orca
51)     gnome-power-manager
52)     gnome-screensaver
53)     gnome-screenshot
54)     gnome-session-bin
55)     gnome-session-canberra
56)     gnome-software
57)     gnome-sudoku
58)     gnome-system-log
59)     gnome-system-monitor
60)     gnome-terminal
61)     gnome-themes-standard
62)     gnome-themes-standard-data
63)     gnome-user-guide
64)     gnome-user-share
65)     gnupg-agent
66)     gnupg2
67)     grilo-plugins-0.2-base
68)     gstreamer1.0-clutter-3.0
69)     gstreamer1.0-libav
70)     gstreamer1.0-plugins-bad
71)     gstreamer1.0-plugins-bad-faad
72)     gstreamer1.0-plugins-bad-videoparsers
73)     gucharmap
74)     gvfs
75)     gvfs-backends
76)     gvfs-daemons
77)     gvfs-fuse
78)     hud
79)     humanity-icon-theme
80)     ibus
81)     ibus-gtk3
82)     ibus-table
83)     indicator-application
84)     indicator-appmenu
85)     indicator-bluetooth
86)     indicator-keyboard
87)     indicator-printers
88)     language-selector-gnome
89)     libaccount-plugin-1.0-0
90)     libaccount-plugin-generic-oauth
91)     libaccount-plugin-google
92)     libappindicator3-1
93)     libavahi-ui-gtk3-0
94)     libavfilter-ffmpeg5
95)     libcanberra-gtk3-0
96)     libcanberra-gtk3-module
97)     libcheese-gtk25
98)     libcheese8
99)     libclutter-1.0-0
100     libclutter-gst-3.0-0
101     libclutter-gtk-1.0-0
102     libcogl-pango20
103     libcogl-path20
104     libcogl20
105     libedataserverui-1.2-1
106     libegl1-mesa
107     libevdocument3-4
108     libevview3-3
109     libgail-3-0
110     libgcr-ui-3-1
111     libgl1-mesa-dri
112     libgl1-mesa-glx
113     libglew1.13
114     libglewmx1.13
115     libglu1-mesa
116     libgmime-2.6-0
117     libgnome-bluetooth13
118     libgnome-desktop-3-12
119     libgnomekbd8
120     libgpgme11
121     libgrilo-0.2-1
122     libgstreamer-plugins-bad1.0-0
123     libgtk-3-0
124     libgtk-3-bin
125     libgtk-3-common
126     libgtkglext1
127     libgtkmm-3.0-1v5
128     libgtksourceview-3.0-1
129     libgtkspell3-3-0
130     libgucharmap-2-90-7
131     libgweather-3-6
132     libido3-0.1-0
133     libindicator3-7
134     libllvm3.8
135     libmetacity-private3a
136     libnautilus-extension1a
137     libnm-gtk0
138     libnma0
139     libnux-4.0-0
140     libopencv-calib3d2.4v5
141     libopencv-contrib2.4v5
142     libopencv-core2.4v5
143     libopencv-features2d2.4v5
144     libopencv-flann2.4v5
145     libopencv-highgui2.4v5
146     libopencv-imgproc2.4v5
147     libopencv-legacy2.4v5
148     libopencv-ml2.4v5
149     libopencv-objdetect2.4v5
150     libopencv-video2.4v5
151     liboxideqt-qmlplugin
152     liboxideqtcore0
153     liboxideqtquick0
154     libpeas-1.0-0
155     libpeas-1.0-0-python3loader
156     libqt5feedback5
157     libqt5gui5
158     libqt5multimedia5
159     libqt5opengl5
160     libqt5printsupport5
161     libqt5quick5
162     libqt5quicktest5
163     libqt5svg5
164     libqt5webkit5
165     libqt5widgets5
166     libqt5x11extras5
167     libreoffice-avmedia-backend-gstreamer
168     libreoffice-base-core
169     libreoffice-calc
170     libreoffice-core
171     libreoffice-draw
172     libreoffice-gnome
173     libreoffice-gtk
174     libreoffice-help-en-us
175     libreoffice-impress
176     libreoffice-math
177     libreoffice-ogltrans
178     libreoffice-pdfimport
179     libreoffice-writer
180     librhythmbox-core9
181     libtimezonemap1
182     libtotem-plparser18
183     libtotem0
184     libubuntugestures5
185     libubuntutoolkit5
186     libunity-control-center1
187     libunity-core-6.0-9
188     libunity-gtk3-parser0
189     libunity-misc4
190     libunity-settings-daemon1
191     libunity-webapps0
192     libvte-2.91-0
193     libwayland-egl1-mesa
194     libwebkit2gtk-4.0-37
195     libwebkit2gtk-4.0-37-gtk2
196     libwnck-3-0
197     libxatracker2
198     libyelp0
199     light-themes
200     mesa-vdpau-drivers
201     mousetweaks
202     nautilus
203     nautilus-sendto
204     nautilus-share
205     network-manager-gnome
206     network-manager-pptp-gnome
207     notify-osd
208     nux-tools
209     onboard
210     onboard-data
211     pinentry-gnome3
212     policykit-1-gnome
213     pyotherside
214     python3-aptdaemon.gtk3widgets
215     python3-uno
216     qml-module-io-thp-pyotherside
217     qml-module-qtfeedback
218     qml-module-qtgraphicaleffects
219     qml-module-qtquick-layouts
220     qml-module-qtquick-window2
221     qml-module-qtquick2
222     qml-module-qttest
223     qml-module-ubuntu-components
224     qml-module-ubuntu-layouts
225     qml-module-ubuntu-onlineaccounts
226     qml-module-ubuntu-performancemetrics
227     qml-module-ubuntu-test
228     qml-module-ubuntu-web
229     qmlscene
230     qtdeclarative5-accounts-plugin
231     qtdeclarative5-dev-tools
232     qtdeclarative5-qtquick2-plugin
233     qtdeclarative5-test-plugin
234     qtdeclarative5-ubuntu-ui-toolkit-plugin
235     remmina
236     remmina-plugin-rdp
237     remmina-plugin-vnc
238     rhythmbox
239     rhythmbox-plugin-zeitgeist
240     rhythmbox-plugins
241     seahorse
242     session-shortcuts
243     sessioninstaller
244     shotwell
245     signon-ui
246     signon-ui-x11
247     simple-scan
248     software-properties-gtk
249     synaptic
250     system-config-printer-gnome
251     totem
252     totem-plugins
253     transmission-gtk
254     ubuntu-artwork
255     ubuntu-desktop
256     ubuntu-docs
257     ubuntu-mono
258     ubuntu-release-upgrader-gtk
259     ubuntu-session
260     ubuntu-software
261     unity
262     unity-asset-pool
263     unity-control-center
264     unity-control-center-signon
265     unity-greeter
266     unity-gtk3-module
267     unity-scope-calculator
268     unity-scope-gdrive
269     unity-scope-manpages
270     unity-services
271     unity-settings-daemon
272     unity-tweak-tool
273     unity-webapps-common
274     unity-webapps-qml
275     unity-webapps-service
276     update-manager
277     update-notifier
278     usb-creator-gtk
279     va-driver-all
280     vdpau-driver-all
281     vdpau-va-driver
282     vino
283     vlc
284     webapp-container
285     webbrowser-app
286     x11-utils
287     xdg-user-dirs-gtk
288     xdiagnose
289     xorg
290     xserver-xorg
291     xserver-xorg-core
292     xserver-xorg-input-all
293     xserver-xorg-input-evdev
294     xserver-xorg-input-synaptics
295     xserver-xorg-input-vmmouse
296     xserver-xorg-input-wacom
297     xserver-                                                                 
```
  And many other packages that cannot fit into this post.

---

### Post by QIII on 2016-04-24
Hello!

What release of Ubuntu are you using?

Would you please do

```
sudo apt-get update && sudo apt-get dist-upgrade
```

and post the results if there are warnings or errors?

---

### Post by chewyboy000 on 2016-04-24
I am using the latest release of Ubuntu 16.04 LTS. When I run the command I get no errors but it looks like it is shorter then it usually is when updating updating/reloading.

```
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease
Hit:2 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                     
Hit:3 [http://repository.spotify.com](http://repository.spotify.com) stable InRelease                           
Reading package lists... Done            
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

