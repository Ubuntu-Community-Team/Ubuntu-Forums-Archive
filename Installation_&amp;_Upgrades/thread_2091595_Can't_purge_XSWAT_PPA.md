---
title: "Can't purge XSWAT PPA"
date: 2012-12-05
forum: Installation &amp; Upgrades
---

### Post by frogotronic on 2012-12-05
ppa-purge is broken for XSWAT??


```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Release 'precise' for 'libdrm-nouveau2' was not found
Unable to find an archive "precise" for the package "libdrm-nouveau2"
Unable to find an archive "precise" for the package "libdrm-nouveau2"
The following packages will be DOWNGRADED:
  libdrm-dev libdrm-intel1{b} libdrm-nouveau1a libdrm-radeon1{b} libdrm2{b} libegl1-mesa libgbm1 libgl1-mesa-dev libgl1-mesa-dri{b} libgl1-mesa-glx{b} libglapi-mesa{b} 
  libgles2-mesa libkms1 libwayland0 libxatracker1 mesa-common-dev xdiagnose xserver-xorg-video-ati xserver-xorg-video-intel xserver-xorg-video-nouveau 
  xserver-xorg-video-radeon 
The following packages will be REMOVED:
  libdrm-nouveau2{u} libtxc-dxtn-s2tc0{u} libxcb-glx0-dev{u} libxxf86vm-dev{u} x11proto-xf86vidmode-dev{u} 
The following packages are RECOMMENDED but will NOT be installed:
  libegl1-mesa-drivers 
0 packages upgraded, 0 newly installed, 21 downgraded, 5 to remove and 3 not upgraded.
Need to get 6,154 kB of archives. After unpacking 22.3 MB will be freed.
The following packages have unmet dependencies:
 libdrm-radeon1 : Breaks: libdrm-radeon1:i386 (!= 2.4.32-1ubuntu1) but 2.4.39-0ubuntu1 is installed.
 libdrm-radeon1:i386 : Breaks: libdrm-radeon1 (!= 2.4.39-0ubuntu1) but 2.4.32-1ubuntu1 is to be installed.
 libgl1-mesa-dri : Breaks: libgl1-mesa-dri:i386 (!= 8.0.2-0ubuntu3) but 9.0-0ubuntu1 is installed.
 libgl1-mesa-dri:i386 : Breaks: libgl1-mesa-dri (!= 9.0-0ubuntu1) but 8.0.2-0ubuntu3 is to be installed.
 libgl1-mesa-glx : Breaks: libgl1-mesa-glx:i386 (!= 8.0.2-0ubuntu3) but 9.0-0ubuntu1 is installed.
 libgl1-mesa-glx:i386 : Breaks: libgl1-mesa-glx (!= 9.0-0ubuntu1) but 8.0.2-0ubuntu3 is to be installed.
 libglapi-mesa : Breaks: libglapi-mesa:i386 (!= 8.0.2-0ubuntu3) but 9.0-0ubuntu1 is installed.
 libglapi-mesa:i386 : Breaks: libglapi-mesa (!= 9.0-0ubuntu1) but 8.0.2-0ubuntu3 is to be installed.
 libdrm2 : Breaks: libdrm2:i386 (!= 2.4.32-1ubuntu1) but 2.4.39-0ubuntu1 is installed.
 libdrm2:i386 : Breaks: libdrm2 (!= 2.4.39-0ubuntu1) but 2.4.32-1ubuntu1 is to be installed.
 libdrm-intel1 : Breaks: libdrm-intel1:i386 (!= 2.4.32-1ubuntu1) but 2.4.39-0ubuntu1 is installed.
 libdrm-intel1:i386 : Breaks: libdrm-intel1 (!= 2.4.39-0ubuntu1) but 2.4.32-1ubuntu1 is to be installed.
Internal error: the solver Install(espeak:i386 1.46.02-0ubuntu1 <espeak-data:amd64 1.46.02-0ubuntu1 -S> {espeak:amd64 1.46.02-0ubuntu1 espeak:i386 1.46.02-0ubuntu1}>) of a supposedly unresolved dependency is already installed in step 139
Internal error: the solver Install(espeak:i386 1.46.02-0ubuntu1 <espeak-data:amd64 1.46.02-0ubuntu1 -S> {espeak:amd64 1.46.02-0ubuntu1 espeak:i386 1.46.02-0ubuntu1}>) of a supposedly unresolved dependency is already installed in step 238
Internal error: the solver Install(espeak:i386 1.46.02-0ubuntu1 <espeak-data:amd64 1.46.02-0ubuntu1 -S> {espeak:amd64 1.46.02-0ubuntu1 espeak:i386 1.46.02-0ubuntu1}>) of a supposedly unresolved dependency is already installed in step 262
Internal error: the solver Install(espeak:i386 1.46.02-0ubuntu1 <espeak-data:amd64 1.46.02-0ubuntu1 -S> {espeak:amd64 1.46.02-0ubuntu1 espeak:i386 1.46.02-0ubuntu1}>) of a supposedly unresolved dependency is already installed in step 410
open: 130; closed: 722; defer: 61; conflict: 113                                                                                                                                .Internal error: the solver Install(fontconfig-config:amd64 2.8.0-3ubuntu9 <libfontconfig1:i386 2.8.0-3ubuntu9 -> {fontconfig-config:amd64 2.8.0-3ubuntu9}>) of a supposedly unresolved dependency is already installed in step 1083
open: 320; closed: 1561; defer: 215; conflict: 457                                                                                                                              oThe following actions will resolve these dependencies:

       Remove the following packages:                                                                                           
1)       acroread                                                                                                               
2)       bluez-alsa:i386                                                                                                        
3)       brhl2170wlpr:i386                                                                                                      
4)       cupswrapperhl2170w:i386                                                                                                
5)       glib-networking:i386                                                                                                   
6)       google-earth-stable                                                                                                    
7)       gstreamer0.10-plugins-base:i386                                                                                        
8)       gstreamer0.10-plugins-good:i386                                                                                        
9)       gstreamer0.10-x:i386                                                                                                   
10)      gtk2-engines:i386                                                                                                      
11)      gtk2-engines-murrine:i386                                                                                              
12)      gtk2-engines-oxygen:i386                                                                                               
13)      gtk2-engines-pixbuf:i386                                                                                               
14)      gvfs:i386                                                                                                              
15)      gvfs-libs:i386                                                                                                         
16)      ia32-crossover                                                                                                         
17)      ia32-libs                                                                                                              
18)      ia32-libs-multiarch:i386                                                                                               
19)      ibus-gtk:i386                                                                                                          
20)      libaa1:i386                                                                                                            
21)      libacl1:i386                                                                                                           
22)      libao4:i386                                                                                                            
23)      libasn1-8-heimdal:i386                                                                                                 
24)      libasound2:i386                                                                                                        
25)      libasound2-plugins:i386                                                                                                
26)      libasyncns0:i386                                                                                                       
27)      libatk1.0-0:i386                                                                                                       
28)      libattr1:i386                                                                                                          
29)      libaudio2:i386                                                                                                         
30)      libaudiofile1:i386                                                                                                     
31)      libavahi-client3:i386                                                                                                  
32)      libavahi-common3:i386                                                                                                  
33)      libavc1394-0:i386                                                                                                      
34)      libbz2-1.0:i386                                                                                                        
35)      libc6:i386                                                                                                             
36)      libcaca0:i386                                                                                                          
37)      libcairo-gobject2:i386                                                                                                 
38)      libcairo2:i386                                                                                                         
39)      libcanberra-gtk-module:i386                                                                                            
40)      libcanberra-gtk0:i386                                                                                                  
41)      libcanberra0:i386                                                                                                      
42)      libcap2:i386                                                                                                           
43)      libcapi20-3:i386                                                                                                       
44)      libcdparanoia0:i386                                                                                                    
45)      libcomerr2:i386                                                                                                        
46)      libcroco3:i386                                                                                                         
47)      libcups2:i386                                                                                                          
48)      libcupsimage2:i386                                                                                                     
49)      libcurl3:i386                                                                                                          
50)      libdatrie1:i386                                                                                                        
51)      libdb5.1:i386                                                                                                          
52)      libdbus-1-3:i386                                                                                                       
53)      libdbus-glib-1-2:i386                                                                                                  
54)      libdbusmenu-qt2:i386                                                                                                   
55)      libdrm-intel1:i386                                                                                                     
56)      libdrm-nouveau2:i386                                                                                                   
57)      libdrm-radeon1:i386                                                                                                    
58)      libdrm2:i386                                                                                                           
59)      libdv4:i386                                                                                                            
60)      libesd0:i386                                                                                                           
61)      libexif12:i386                                                                                                         
62)      libexpat1:i386                                                                                                         
63)      libffi6:i386                                                                                                           
64)      libflac8:i386                                                                                                          
65)      libfontconfig1:i386                                                                                                    
66)      libfreetype6:i386                                                                                                      
67)      libgail-common:i386                                                                                                    
68)      libgail18:i386                                                                                                         
69)      libgcc1:i386                                                                                                           
70)      libgconf-2-4:i386                                                                                                      
71)      libgcrypt11:i386                                                                                                       
72)      libgd2-xpm:i386                                                                                                        
73)      libgdbm3:i386                                                                                                          
74)      libgdk-pixbuf2.0-0:i386                                                                                                
75)      libgettextpo0:i386                                                                                                     
76)      libgif4:i386                                                                                                           
77)      libgl1-mesa-dri:i386                                                                                                   
78)      libgl1-mesa-glx:i386                                                                                                   
79)      libglapi-mesa:i386                                                                                                     
80)      libglib2.0-0:i386                                                                                                      
81)      libglu1-mesa:i386                                                                                                      
82)      libgnome-keyring0:i386                                                                                                 
83)      libgnutls26:i386                                                                                                       
84)      libgomp1:i386                                                                                                          
85)      libgpg-error0:i386                                                                                                     
86)      libgphoto2-2:i386                                                                                                      
87)      libgphoto2-port0:i386                                                                                                  
88)      libgpm2:i386                                                                                                           
89)      libgssapi-krb5-2:i386                                                                                                  
90)      libgssapi3-heimdal:i386                                                                                                
91)      libgstreamer-plugins-base0.10-0:i386                                                                                   
92)      libgstreamer0.10-0:i386                                                                                                
93)      libgtk2.0-0:i386                                                                                                       
94)      libgudev-1.0-0:i386                                                                                                    
95)      libhcrypto4-heimdal:i386                                                                                               
96)      libheimbase1-heimdal:i386                                                                                              
97)      libheimntlm0-heimdal:i386                                                                                              
98)      libhx509-5-heimdal:i386                                                                                                
99)      libibus-1.0-0:i386                                                                                                     
100)     libice6:i386                                                                                                           
101)     libidn11:i386                                                                                                          
102)     libiec61883-0:i386                                                                                                     
103)     libieee1284-3:i386                                                                                                     
104)     libjack-jackd2-0:i386                                                                                                  
105)     libjasper1:i386                                                                                                        
106)     libjpeg-turbo8:i386                                                                                                    
107)     libjpeg8:i386                                                                                                          
108)     libjson0:i386                                                                                                          
109)     libk5crypto3:i386                                                                                                      
110)     libkeyutils1:i386                                                                                                      
111)     libkrb5-26-heimdal:i386                                                                                                
112)     libkrb5-3:i386                                                                                                         
113)     libkrb5support0:i386                                                                                                   
114)     liblcms1:i386                                                                                                          
115)     libldap-2.4-2:i386                                                                                                     
116)     libllvm3.1:i386                                                                                                        
117)     libltdl7:i386                                                                                                          
118)     libmad0:i386                                                                                                           
119)     libmikmod2:i386                                                                                                        
120)     libmng1:i386                                                                                                           
121)     libmpg123-0:i386                                                                                                       
122)     libmysqlclient18:i386                                                                                                  
123)     libncurses5:i386                                                                                                       
124)     libncursesw5:i386                                                                                                      
125)     libnspr4:i386                                                                                                          
126)     libnss3:i386                                                                                                           
127)     libodbc1:i386                                                                                                          
128)     libogg0:i386                                                                                                           
129)     libopenal1:i386                                                                                                        
130)     liborc-0.4-0:i386                                                                                                      
131)     libosmesa6:i386                                                                                                        
132)     libp11-kit0:i386                                                                                                       
133)     libpango1.0-0:i386                                                                                                     
134)     libpciaccess0:i386                                                                                                     
135)     libpcre3:i386                                                                                                          
136)     libpixman-1-0:i386                                                                                                     
137)     libpng12-0:i386                                                                                                        
138)     libproxy1:i386                                                                                                         
139)     libpulse-mainloop-glib0:i386                                                                                           
140)     libpulse0:i386                                                                                                         
141)     libpulsedsp:i386                                                                                                       
142)     libqt4-dbus:i386                                                                                                       
143)     libqt4-declarative:i386                                                                                                
144)     libqt4-designer:i386                                                                                                   
145)     libqt4-network:i386                                                                                                    
146)     libqt4-opengl:i386                                                                                                     
147)     libqt4-qt3support:i386                                                                                                 
148)     libqt4-script:i386                                                                                                     
149)     libqt4-scripttools:i386                                                                                                
150)     libqt4-sql:i386                                                                                                        
151)     libqt4-sql-mysql:i386                                                                                                  
152)     libqt4-svg:i386                                                                                                        
153)     libqt4-test:i386                                                                                                       
154)     libqt4-xml:i386                                                                                                        
155)     libqt4-xmlpatterns:i386                                                                                                
156)     libqtcore4:i386                                                                                                        
157)     libqtgui4:i386                                                                                                         
158)     libqtwebkit4:i386                                                                                                      
159)     libraw1394-11:i386                                                                                                     
160)     libroken18-heimdal:i386                                                                                                
161)     librsvg2-2:i386                                                                                                        
162)     librsvg2-common:i386                                                                                                   
163)     librtmp0:i386                                                                                                          
164)     libsamplerate0:i386                                                                                                    
165)     libsane:i386                                                                                                           
166)     libsasl2-2:i386                                                                                                        
167)     libsasl2-modules:i386                                                                                                  
168)     libsdl-image1.2:i386                                                                                                   
169)     libsdl-mixer1.2:i386                                                                                                   
170)     libsdl-net1.2:i386                                                                                                     
171)     libsdl-ttf2.0-0:i386                                                                                                   
172)     libsdl1.2debian:i386                                                                                                   
173)     libselinux1:i386                                                                                                       
174)     libshout3:i386                                                                                                         
175)     libslang2:i386                                                                                                         
176)     libsm6:i386                                                                                                            
177)     libsndfile1:i386                                                                                                       
178)     libsoup-gnome2.4-1:i386                                                                                                
179)     libsoup2.4-1:i386                                                                                                      
180)     libspeex1:i386                                                                                                         
181)     libspeexdsp1:i386                                                                                                      
182)     libsqlite3-0:i386                                                                                                      
183)     libssl0.9.8:i386                                                                                                       
184)     libssl1.0.0:i386                                                                                                       
185)     libstdc++5:i386                                                                                                        
186)     libstdc++6:i386                                                                                                        
187)     libtag1-vanilla:i386                                                                                                   
188)     libtag1c2a:i386                                                                                                        
189)     libtasn1-3:i386                                                                                                        
190)     libtdb1:i386                                                                                                           
191)     libthai0:i386                                                                                                          
192)     libtheora0:i386                                                                                                        
193)     libtiff4:i386                                                                                                          
194)     libtinfo5:i386                                                                                                         
195)     libtxc-dxtn-s2tc0:i386                                                                                                 
196)     libudev0:i386                                                                                                          
197)     libunistring0:i386                                                                                                     
198)     libusb-0.1-4:i386                                                                                                      
199)     libuuid1:i386                                                                                                          
200)     libv4l-0:i386                                                                                                          
201)     libv4lconvert0:i386                                                                                                    
202)     libvisual-0.4-0:i386                                                                                                   
203)     libvisual-0.4-plugins:i386                                                                                             
204)     libvorbis0a:i386                                                                                                       
205)     libvorbisenc2:i386                                                                                                     
206)     libvorbisfile3:i386                                                                                                    
207)     libwavpack1:i386                                                                                                       
208)     libwind0-heimdal:i386                                                                                                  
209)     libwrap0:i386                                                                                                          
210)     libx11-6:i386                                                                                                          
211)     libx11-xcb1:i386                                                                                                       
212)     libxau6:i386                                                                                                           
213)     libxaw7:i386                                                                                                           
214)     libxcb-glx0:i386                                                                                                       
215)     libxcb-render0:i386                                                                                                    
216)     libxcb-shm0:i386                                                                                                       
217)     libxcb1:i386                                                                                                           
218)     libxcomposite1:i386                                                                                                    
219)     libxcursor1:i386                                                                                                       
220)     libxdamage1:i386                                                                                                       
221)     libxdmcp6:i386                                                                                                         
222)     libxext6:i386                                                                                                          
223)     libxfixes3:i386                                                                                                        
224)     libxft2:i386                                                                                                           
225)     libxi6:i386                                                                                                            
226)     libxinerama1:i386                                                                                                      
227)     libxml2:i386                                                                                                           
228)     libxmu6:i386                                                                                                           
229)     libxp6:i386                                                                                                            
230)     libxpm4:i386                                                                                                           
231)     libxrandr2:i386                                                                                                        
232)     libxrender1:i386                                                                                                       
233)     libxslt1.1:i386                                                                                                        
234)     libxss1:i386                                                                                                           
235)     libxt6:i386                                                                                                            
236)     libxtst6:i386                                                                                                          
237)     libxv1:i386                                                                                                            
238)     libxxf86vm1:i386                                                                                                       
239)     netflix-desktop                                                                                                        
240)     nspluginviewer:i386                                                                                                    
241)     nspluginwrapper                                                                                                        
242)     odbcinst1debian2:i386                                                                                                  
243)     playonlinux                                                                                                            
244)     skype:i386                                                                                                             
245)     skype-bin:i386                                                                                                         
246)     sni-qt:i386                                                                                                            
247)     wine                                                                                                                   
248)     wine-compholio:i386                                                                                                    
249)     wine-gecko1.4:i386                                                                                                     
250)     wine1.4                                                                                                                
251)     wine1.4-amd64                                                                                                          
252)     wine1.4-common                                                                                                         
253)     wine1.4-i386:i386                                                                                                      
254)     xaw3dg:i386                                                                                                            
255)     zlib1g:i386                                                                                                            

       Leave the following dependencies unresolved:                                                                             
256)     winetricks recommends wine1.4 | wine | cxoffice5 | cxgames5                                                            
257)     wine-gecko1.4 recommends wine1.4-amd64                                                                                 
258)     libcanberra-gtk0:i386 recommends libcanberra-gtk-module:i386                                                           
259)     libncurses5:i386 recommends libgpm2:i386                                                                               
260)     libncursesw5:i386 recommends libgpm2:i386                                                                              
261)     libslang2:i386 recommends libpng12-0:i386                                                                              
262)     libvisual-0.4-0:i386 recommends libvisual-0.4-plugins:i386                                                             
263)     libgphoto2-2:i386 recommends udev:i386 (>= 0.175)                                                                      
264)     libgphoto2-2:i386 recommends libgphoto2-l10n:i386 (>= 2.4.13-1ubuntu1.2)                                               
265)     libqt4-dbus:i386 recommends qdbus:i386 (= 4:4.8.1-0ubuntu4.3)                                                          
266)     libqt4-sql:i386 recommends libqt4-sql-mysql:i386 | libqt4-sql-odbc:i386 | libqt4-sql-psql:i386 | libqt4-sql-sqlite:i386
267)     wine1.4-i386:i386 recommends libfontconfig1:i386 | libfontconfig:i386                                                  
268)     wine1.4-i386:i386 recommends libsane:i386                                                                              
269)     wine1.4-i386:i386 recommends wine-gecko1.4:i386                                                                        
270)     skype-bin:i386 recommends libasound2-plugins:i386                                                                      
271)     gstreamer0.10-plugins-good:i386 recommends gstreamer0.10-x:i386                                                        
272)     wine-compholio:i386 recommends libsane:i386                                                                            
273)     libgl1-mesa-glx:i386 recommends libgl1-mesa-dri:i386 (>= 7.2)                                                          


Accept this solution? [Y/n/q/?] q
```

---

### Post by zvacet on 2012-12-05
You can try to purge PPA with [this.]("http://maketecheasier.com/search-manage-ppas-with-y-ppa-manager/2011/01/20")If you want to do it from terminal then see [here.]("http://www.webupd8.org/2009/12/remove-ppa-repositories-via-command.html")

---

