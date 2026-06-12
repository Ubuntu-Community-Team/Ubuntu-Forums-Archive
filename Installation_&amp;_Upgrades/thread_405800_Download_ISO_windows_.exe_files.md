---
title: "Download ISO windows .exe files"
date: 2007-04-10
forum: Installation &amp; Upgrades
---

### Post by ubuntumaybe on 2007-04-10
Hi,

I have a duel boot laptop with windows XP and kubuntu 6.06. I downloaded the 6.10 .ISO file to windows XP. I used a downloaded XP program to create the folders and file system contained in the .ISO file. When I attempted to upgrade from my current 6.06 version using the new 6.10 cd I could not. I examined the 6.10 cd file system and found a number of windows .exe files. Did I download the wrong .ISO? I do not have a broadband connection. I would like to upgrade from 6.06 to 6.10. What must I do? Thanks.

Joe

---

### Post by chewearn on 2007-04-10
You have to burn the iso as a disc image to your cd.  Creating folders and copy the files over will not work.

There should be some Windows .exe files in the cd; this is for windows user to try some of the free software that comes with the disc, like firefox, etc.

---

### Post by ubuntumaybe on 2007-04-11
HI,

I guess I did not make myself clear. I actually created the disc image but when I viewed the files in the folder they were windows .exe files. Shoud that be correct? Thanks.

---

### Post by zvacet on 2007-04-11
Just download iso image and burn it very slow without tuch anything on it.Therre is no win exe.files in Ubuntu iso image.

---

### Post by chewearn on 2007-04-11
> **zvacet said:**
> Therre is no win exe.files in Ubuntu iso image.

That's not entirely true.  When I pops in the ubuntu 6.10 disc into a WinXP, it launches an application, which allows me to install abiword, firefox, etc.

I attached some screenshots from windows.

Anyway, back to OP question; did you set the Synaptic to use your CD as the source repo?  (In Synaptic menu > Edit > Add CD-ROM)

---

### Post by ubuntumaybe on 2007-04-11
Hi,

I added the cd to list but I cannot see the files I am looking for like GIMP. I executed the tree /F command in a dos prompt window and saved the results to a file. I have pasted the results below. As you will see there are some .deb files but a number of the files are .exe files for windows specially GIMP. Let me know what you think. Thanks.

---------------------  START --------------------------------------

Folder PATH listing for volume Ubuntu 6.10 i386
Volume serial number is 0006EE48 BF50:53F3
D:.
³   README.diskdefines
³   autorun.inf
³   cdromupgrade
³   md5sum.txt
³   start.bmp
³   start.exe
³   start.ini
³   ubuntu
³   ubuntu.ico
³   
ÃÄÄÄ.disk
³       info
³       
ÃÄÄÄbin
³   ³   Launch.exe
³   ³   License.txt
³   ³   SetDefault.exe
³   ³   gkgfx.dll
³   ³   js3250.dll
³   ³   jsj3250.dll
³   ³   k-meleon.exe
³   ³   k-meleon.exe.manifest
³   ³   mozctl.dll
³   ³   mozctlx.dll
³   ³   mozilla-ipcd.exe
³   ³   mozz.dll
³   ³   nspr4.dll
³   ³   nssckbi.dll
³   ³   plc4.dll
³   ³   plds4.dll
³   ³   readme.html
³   ³   smime3.dll
³   ³   softokn3.chk
³   ³   ssl3.dll
³   ³   start.ini
³   ³   start2.exe
³   ³   uninstall.exe
³   ³   xpcom.dll
³   ³   xpcom_compat.dll
³   ³   
³   ÃÄÄÄchrome
³   ³   ³   aggreg8.jar
³   ³   ³   chrome.rdf
³   ³   ³   classic.jar
³   ³   ³   comm.jar
³   ³   ³   en-US.jar
³   ³   ³   en-win.jar
³   ³   ³   flashblock.jar
³   ³   ³   installed-chrome.txt
³   ³   ³   pipnss.jar
³   ³   ³   pippki.jar
³   ³   ³   toolkit.jar
³   ³   ³   us.jar
³   ³   ³   
³   ³   ÃÄÄÄaggreg8
³   ³   ³   ÀÄÄÄcontent
³   ³   ³           rssfeeds.rdf
³   ³   ³           
³   ³   ÀÄÄÄoverlayinfo
³   ³       ÃÄÄÄbrowser
³   ³       ³   ÀÄÄÄcontent
³   ³       ³           overlays.rdf
³   ³       ³           
³   ³       ÃÄÄÄcommunicator
³   ³       ³   ÀÄÄÄcontent
³   ³       ³           overlays.rdf
³   ³       ³           
³   ³       ÃÄÄÄmessenger
³   ³       ³   ÀÄÄÄcontent
³   ³       ³           overlays.rdf
³   ³       ³           
³   ³       ÀÄÄÄnavigator
³   ³           ÀÄÄÄcontent
³   ³                   overlays.rdf
³   ³                   
³   ÃÄÄÄcomponents
³   ³       accessibility-msaa.xpt
³   ³       accessibility.xpt
³   ³       appshell.dll
³   ³       appshell.xpt
³   ³       caps.dll
³   ³       caps.xpt
³   ³       chardet.xpt
³   ³       chrome.dll
³   ³       composer.dll
³   ³       composer.xpt
³   ³       compreg.dat
³   ³       content_base.xpt
³   ³       cookie.dll
³   ³       cookie.xpt
³   ³       docshell.dll
³   ³       docshell_base.xpt
³   ³       dom.xpt
³   ³       dom_base.xpt
³   ³       dom_core.xpt
³   ³       dom_css.xpt
³   ³       dom_events.xpt
³   ³       dom_html.xpt
³   ³       dom_range.xpt
³   ³       dom_stylesheets.xpt
³   ³       dom_traversal.xpt
³   ³       dom_views.xpt
³   ³       dom_xbl.xpt
³   ³       dom_xpath.xpt
³   ³       dom_xul.xpt
³   ³       editor.xpt
³   ³       embed_base.xpt
³   ³       embed_lite.dll
³   ³       embedcomponents.dll
³   ³       gfx.xpt
³   ³       gkgfxwin.dll
³   ³       gklayout.dll
³   ³       gkparser.dll
³   ³       gkwidget.dll
³   ³       i18n.dll
³   ³       imglib2.dll
³   ³       imglib2.xpt
³   ³       intl.xpt
³   ³       intlcmpt.dll
³   ³       intlcmpt.xpt
³   ³       ipcd.xpt
³   ³       ipcdc.dll
³   ³       jar.xpt
³   ³       jar50.dll
³   ³       jsconsole-clhandler.js
³   ³       jsconsole.xpt
³   ³       jsd3250.dll
³   ³       jsdservice.xpt
³   ³       jsurl.xpt
³   ³       layout_base.xpt
³   ³       layout_xul.xpt
³   ³       layout_xul_tree.xpt
³   ³       locale.xpt
³   ³       necko.dll
³   ³       necko.xpt
³   ³       necko2.dll
³   ³       necko_about.xpt
³   ³       necko_cache.xpt
³   ³       necko_cookie.xpt
³   ³       necko_data.xpt
³   ³       necko_dns.xpt
³   ³       necko_file.xpt
³   ³       necko_ftp.xpt
³   ³       necko_http.xpt
³   ³       necko_jar.xpt
³   ³       necko_res.xpt
³   ³       necko_strconv.xpt
³   ³       necko_viewsource.xpt
³   ³       nsProxyAutoConfig.js
³   ³       nsSidebar.js
³   ³       oji.dll
³   ³       oji.xpt
³   ³       p3p.dll
³   ³       p3p.xpt
³   ³       pipboot.dll
³   ³       pipboot.xpt
³   ³       pipnss.xpt
³   ³       pippki.dll
³   ³       pippki.xpt
³   ³       pref.xpt
³   ³       profile.dll
³   ³       profile.xpt
³   ³       rdf.dll
³   ³       rdf.xpt
³   ³       shistory.xpt
³   ³       sidebar.xpt
³   ³       txmgr.dll
³   ³       txmgr.xpt
³   ³       txtsvc.xpt
³   ³       typeaheadfind.dll
³   ³       typeaheadfind.xpt
³   ³       uconv.dll
³   ³       uconv.xpt
³   ³       ucvmath.dll
³   ³       unicharutil.xpt
³   ³       universalchardet.dll
³   ³       uriloader.xpt
³   ³       wallet.dll
³   ³       wallet.xpt
³   ³       walleteditor.xpt
³   ³       walletpreview.xpt
³   ³       webBrowser_core.xpt
³   ³       webbrwsr.dll
³   ³       widget.xpt
³   ³       windowwatcher.xpt
³   ³       xmlextras.dll
³   ³       xmlextras.xpt
³   ³       xpc3250.dll
³   ³       xpcom_base.xpt
³   ³       xpcom_compat_c.dll
³   ³       xpcom_components.xpt
³   ³       xpcom_ds.xpt
³   ³       xpcom_io.xpt
³   ³       xpcom_obsolete.xpt
³   ³       xpcom_thread.xpt
³   ³       xpcom_xpti.xpt
³   ³       xpconnect.xpt
³   ³       xppref32.dll
³   ³       xpti.dat
³   ³       xuldoc.xpt
³   ³       
³   ÃÄÄÄdefaults
³   ³   ÃÄÄÄautoconfig
³   ³   ³       platform.js
³   ³   ³       prefcalls.js
³   ³   ³       
³   ³   ÃÄÄÄpref
³   ³   ³       all.js
³   ³   ³       security-prefs.js
³   ³   ³       winpref.js
³   ³   ³       
³   ³   ÃÄÄÄprofile
³   ³   ³   ³   Prefs.js
³   ³   ³   ³   accel.cfg
³   ³   ³   ³   cookies.txt
³   ³   ³   ³   cookperm.txt
³   ³   ³   ³   history.txt
³   ³   ³   ³   localstore.rdf
³   ³   ³   ³   macros.cfg
³   ³   ³   ³   menus.cfg
³   ³   ³   ³   mimeTypes.rdf
³   ³   ³   ³   user.js
³   ³   ³   ³   
³   ³   ³   ÀÄÄÄchrome
³   ³   ³           userChrome.css
³   ³   ³           userContent.css
³   ³   ³           
³   ³   ÀÄÄÄwallet
³   ³           DistinguishedSchema.tbl
³   ³           FieldSchema.tbl
³   ³           PositionalSchema.tbl
³   ³           SchemaConcat.tbl
³   ³           SchemaStrings.tbl
³   ³           StateSchema.tbl
³   ³           VcardSchema.tbl
³   ³           
³   ÃÄÄÄgreprefs
³   ³       all.js
³   ³       non-shared.txt
³   ³       security-prefs.js
³   ³       xpinstall.js
³   ³       
³   ÃÄÄÄipc
³   ³   ÀÄÄÄmodules
³   ³           lockmodule.dll
³   ³           transmgr.dll
³   ³           
³   ÃÄÄÄkplugins
³   ³       macros.dll
³   ³       
³   ÃÄÄÄplugins
³   ³       npnul32.dll
³   ³       
³   ÀÄÄÄres
³       ³   EditorOverride.css
³       ³   arrow.gif
³       ³   arrowd.gif
³       ³   broken-image.gif
³       ³   charsetData.properties
³       ³   charsetalias.properties
³       ³   cmessage.txt
³       ³   forms.css
³       ³   grabber.gif
³       ³   html.css
³       ³   langGroups.properties
³       ³   language.properties
³       ³   loading-image.gif
³       ³   mathml.css
³       ³   platform-forms.css
³       ³   quirk.css
³       ³   ua.css
³       ³   viewsource.css
³       ³   wincharset.properties
³       ³   
³       ÃÄÄÄbuiltin
³       ³       htmlBindings.xml
³       ³       platformHTMLBindings.xml
³       ³       
³       ÃÄÄÄdtd
³       ³       mathml.dtd
³       ³       xhtml11.dtd
³       ³       
³       ÃÄÄÄentityTables
³       ³       html40Latin1.properties
³       ³       html40Special.properties
³       ³       html40Symbols.properties
³       ³       htmlEntityVersions.properties
³       ³       mathml20.properties
³       ³       transliterate.properties
³       ³       
³       ÃÄÄÄfonts
³       ³       fontEncoding.properties
³       ³       mathfont.properties
³       ³       mathfontCMEX10.properties
³       ³       mathfontCMSY10.properties
³       ³       mathfontMTExtra.properties
³       ³       mathfontMath1.properties
³       ³       mathfontMath2.properties
³       ³       mathfontMath4.properties
³       ³       mathfontPUA.properties
³       ³       mathfontSymbol.properties
³       ³       
³       ÀÄÄÄhtml
³               gopher-audio.gif
³               gopher-binary.gif
³               gopher-find.gif
³               gopher-image.gif
³               gopher-menu.gif
³               gopher-movie.gif
³               gopher-sound.gif
³               gopher-telnet.gif
³               gopher-text.gif
³               gopher-unknown.gif
³               
ÃÄÄÄcasper
³       filesystem.manifest
³       filesystem.manifest-desktop
³       filesystem.squashfs
³       initrd.gz
³       vmlinuz
³       
ÃÄÄÄdisctree
³   ÃÄÄÄapp_img
³   ³       abiword_01.png
³   ³       abiword_01_tn.png
³   ³       abiword_02.png
³   ³       abiword_02_tn.png
³   ³       firefox_01.png
³   ³       firefox_01_tn.png
³   ³       firefox_02.png
³   ³       firefox_02_tn.png
³   ³       gaim_01.png
³   ³       gaim_01_tn.png
³   ³       gimp_01.png
³   ³       gimp_01_tn.png
³   ³       gimp_02.png
³   ³       gimp_02_tn.png
³   ³       opencd_01.png
³   ³       opencd_01_tn.png
³   ³       opencd_02.png
³   ³       opencd_02_tn.png
³   ³       thunderbird_01.png
³   ³       thunderbird_01_tn.png
³   ³       thunderbird_02.png
³   ³       thunderbird_02_tn.png
³   ³       ubuntu-addapp.png
³   ³       ubuntu-addapp_tn.png
³   ³       ubuntu-desktop.png
³   ³       ubuntu-desktop_tn.png
³   ³       ubuntu-gimp.png
³   ³       ubuntu-gimp_tn.png
³   ³       ubuntu-nautilus.png
³   ³       ubuntu-nautilus_tn.png
³   ³       ubuntu_225.png
³   ³       
³   ÃÄÄÄen
³   ³       abiword.html
³   ³       abiword_install.lch
³   ³       abiword_web.lch
³   ³       aboutgtk.html
³   ³       firefox.html
³   ³       firefox_install.lch
³   ³       firefox_web.lch
³   ³       gaim.html
³   ³       gaim_install.lch
³   ³       gaim_web.lch
³   ³       gimp.html
³   ³       gimp_install.lch
³   ³       gimp_web.lch
³   ³       gtk_install.lch
³   ³       gtk_web.lch
³   ³       home.html
³   ³       opencd.html
³   ³       opencd_web.lch
³   ³       theopencd_web.lch
³   ³       thunderbird.html
³   ³       thunderbird_install.lch
³   ³       thunderbird_web.lch
³   ³       ubuntu.html
³   ³       ubuntu_web.lch
³   ³       
³   ÀÄÄÄincl
³       ³   InfoWindow.html
³       ³   forum_web.lch
³       ³   kmeleon_web.lch
³       ³   orchard_web.lch
³       ³   source_web.lch
³       ³   
³       ÃÄÄÄcss
³       ³       app_page.css
³       ³       common.css
³       ³       info_page.css
³       ³       main_page.css
³       ³       
³       ÃÄÄÄimg
³       ³       abiword.png
³       ³       backarrow.png
³       ³       bkg.jpg
³       ³       body_btm.png
³       ³       bullet.png
³       ³       exit.png
³       ³       firefox.png
³       ³       gaim.png
³       ³       gimp.png
³       ³       globe-s.png
³       ³       gohome.png
³       ³       gtk-big.png
³       ³       gtk.png
³       ³       info-i.png
³       ³       install-s.png
³       ³       install.png
³       ³       opencd.png
³       ³       shadow200.png
³       ³       shadow225.png
³       ³       shadow250.png
³       ³       shadow250b.png
³       ³       thunderbird.png
³       ³       top_amber.png
³       ³       ubuntu-logo-large.png
³       ³       ubuntu-logo-small.png
³       ³       ubuntu.png
³       ³       white.png
³       ³       
³       ÀÄÄÄjs
³               ocd_common.js
³               
ÃÄÄÄdists
³   ³   stable
³   ³   unstable
³   ³   
³   ÀÄÄÄedgy
³       ³   Release
³       ³   Release.gpg
³       ³   
³       ÃÄÄÄmain
³       ³   ÃÄÄÄbinary-i386
³       ³   ³       Packages
³       ³   ³       Packages.gz
³       ³   ³       Release
³       ³   ³       
³       ³   ÃÄÄÄdist-upgrader
³       ³   ³   ÀÄÄÄbinary-all
³       ³   ³           edgy.tar.gz
³       ³   ³           edgy.tar.gz.gpg
³       ³   ³           
³       ³   ÀÄÄÄsource
³       ÀÄÄÄrestricted
³           ÃÄÄÄbinary-i386
³           ³       Packages
³           ³       Packages.gz
³           ³       Release
³           ³       
³           ÀÄÄÄsource
ÃÄÄÄinstall
³       README.sbm
³       mt86plus
³       sbm.bin
³       
ÃÄÄÄisolinux
³       16x16.fnt
³       af.tr
³       ar.tr
³       back.jpg
³       be.tr
³       bg.tr
³       bn.tr
³       boot.cat
³       bootlogo
³       br.tr
³       ca.tr
³       cs.tr
³       csb.tr
³       da.tr
³       de.hlp
³       de.tr
³       el.tr
³       en.hlp
³       en.tr
³       eo.tr
³       es.hlp
³       es.tr
³       et.tr
³       eu.hlp
³       eu.tr
³       f1.txt
³       f10.txt
³       f2.txt
³       f3.txt
³       f3.txt.withgtk
³       f4.txt
³       f4.txt.withgtk
³       f5.txt
³       f6.txt
³       f7.txt
³       f8.txt
³       f9.txt
³       fa.tr
³       fi.hlp
³       fi.tr
³       fil.tr
³       fr.hlp
³       fr.tr
³       ga.tr
³       gl.hlp
³       gl.tr
³       hi.tr
³       hr.tr
³       hu.hlp
³       hu.tr
³       id.hlp
³       id.tr
³       is.tr
³       isolinux.bin
³       isolinux.cfg
³       isolinux.txt
³       it.tr
³       ja.tr
³       ka.hlp
³       ka.tr
³       kn.tr
³       ko.hlp
³       ko.tr
³       ku.tr
³       langlist
³       lt.tr
³       lv.tr
³       mk.tr
³       mn.tr
³       ms.tr
³       nb.tr
³       nds.tr
³       nl.hlp
³       nl.tr
³       oc.tr
³       pl.hlp
³       pl.tr
³       pt.hlp
³       pt.tr
³       pt_BR.hlp
³       pt_BR.tr
³       ro.tr
³       ru.hlp
³       ru.tr
³       sk.hlp
³       sk.tr
³       sl.tr
³       so.tr
³       splash.pcx
³       splash.rle
³       sq.tr
³       sr.tr
³       sv.hlp
³       sv.tr
³       ta.tr
³       th.tr
³       tr.tr
³       uk.tr
³       ur.tr
³       vi.tr
³       zh_CN.hlp
³       zh_CN.tr
³       zh_TW.tr
³       
ÃÄÄÄpics
³       blue-lowerleft.png
³       blue-lowerright.png
³       blue-upperleft.png
³       blue-upperright.png
³       debian.jpg
³       logo-50.jpg
³       red-lowerleft.png
³       red-lowerright.png
³       red-upperleft.png
³       red-upperright.png
³       
ÃÄÄÄpool
³   ÃÄÄÄmain
³   ³   ÃÄÄÄb
³   ³   ³   ÃÄÄÄbpalogin
³   ³   ³   ³       bpalogin_2.0.2-9ubuntu1_i386.deb
³   ³   ³   ³       
³   ³   ³   ÀÄÄÄbuild-essential
³   ³   ³           build-essential_11.3_i386.deb
³   ³   ³           
³   ³   ÃÄÄÄd
³   ³   ³   ÀÄÄÄdpkg
³   ³   ³           dpkg-dev_1.13.22ubuntu7_all.deb
³   ³   ³           
³   ³   ÃÄÄÄe
³   ³   ³   ÀÄÄÄeagle-usb
³   ³   ³           eagle-usb-data_2.1.1-2ubuntu1_all.deb
³   ³   ³           eagle-usb-utils_2.1.1-2ubuntu1_i386.deb
³   ³   ³           
³   ³   ÃÄÄÄf
³   ³   ³   ÀÄÄÄfakeroot
³   ³   ³           fakeroot_1.5.9ubuntu1_i386.deb
³   ³   ³           
³   ³   ÃÄÄÄg
³   ³   ³   ÃÄÄÄgcc-4.1
³   ³   ³   ³       g++-4.1_4.1.1-13ubuntu5_i386.deb
³   ³   ³   ³       libstdc++6-4.1-dev_4.1.1-13ubuntu5_i386.deb
³   ³   ³   ³       
³   ³   ³   ÃÄÄÄgcc-defaults
³   ³   ³   ³       g++_4.1.1-6ubuntu3_i386.deb
³   ³   ³   ³       
³   ³   ³   ÀÄÄÄglibc
³   ³   ³           libc6-dev_2.4-1ubuntu12_i386.deb
³   ³   ³           
³   ³   ÃÄÄÄi
³   ³   ³   ÀÄÄÄisdnutils
³   ³   ³           capiutils_3.9.20060704-1_i386.deb
³   ³   ³           ipppd_3.9.20060704-1_i386.deb
³   ³   ³           isdnutils-base_3.9.20060704-1_i386.deb
³   ³   ³           isdnutils-xtools_3.9.20060704-1_i386.deb
³   ³   ³           libcapi20-3_3.9.20060704-1_i386.deb
³   ³   ³           libcapi20-dev_3.9.20060704-1_i386.deb
³   ³   ³           pppdcapiplugin_3.9.20060704-1_i386.deb
³   ³   ³           
³   ³   ÃÄÄÄl
³   ³   ³   ÃÄÄÄlinux-atm
³   ³   ³   ³       libatm1_2.4.1-17_i386.deb
³   ³   ³   ³       
³   ³   ³   ÃÄÄÄlinux-source-2.6.17
³   ³   ³   ³       linux-libc-dev_2.6.17-10.33_i386.deb
³   ³   ³   ³       
³   ³   ³   ÀÄÄÄlinux-wlan-ng
³   ³   ³           linux-wlan-ng_0.2.5-2ubuntu1_i386.deb
³   ³   ³           
³   ³   ÃÄÄÄn
³   ³   ³   ÃÄÄÄndiswrapper
³   ³   ³   ³       ndiswrapper-common_1.18-1ubuntu2_all.deb
³   ³   ³   ³       ndiswrapper-utils-1.8_1.18-1ubuntu2_i386.deb
³   ³   ³   ³       
³   ³   ³   ÀÄÄÄndiswrapper-1.1
³   ³   ³           ndiswrapper-utils-1.1_1.1-5_i386.deb
³   ³   ³           ndiswrapper-utils_1.1-5_all.deb
³   ³   ³           
³   ³   ÃÄÄÄp
³   ³   ³   ÀÄÄÄpptp-linux
³   ³   ³           pptp-linux_1.7.0-2ubuntu1_i386.deb
³   ³   ³           
³   ³   ÀÄÄÄs
³   ³       ÀÄÄÄsetserial
³   ³               setserial_2.17-43_i386.deb
³   ³               
³   ÀÄÄÄrestricted
³       ÃÄÄÄd
³       ³   ÀÄÄÄdrdsl
³       ³           drdsl_1.2.0-1_i386.deb
³       ³           
³       ÀÄÄÄl
³           ÃÄÄÄlinux-meta
³           ³       avm-fritz-firmware_2.6.17.10_i386.deb
³           ³       
³           ÀÄÄÄlinux-restricted-modules-2.6.17
³                   avm-fritz-firmware-2.6.17-10_3.11+2.6.17.5-11_i386.deb
³                   
ÃÄÄÄpreseed
³       cli.seed
³       ubuntu.seed
³       
ÀÄÄÄprograms
    ÃÄÄÄabiword
    ³       AbiwordSetup.exe
    ³       
    ÃÄÄÄfirefox
    ³       FirefoxSetup.exe
    ³       
    ÃÄÄÄgaim
    ³       GaimSetup.exe
    ³       
    ÃÄÄÄgimp
    ³       GimpSetup.exe
    ³       
    ÃÄÄÄgtk
    ³       GTKSetup.exe
    ³       
    ÀÄÄÄthunderbird
            ThunderbirdSetup.exe

---------------------  END  --------------------------------------

---

### Post by chewearn on 2007-04-12
Unfortunately, I am not sure how the CD repo works.  I once did a thorough examination of the liveCD, I found out that the deb files are "packaged/zipped" inside a large file in the cd, meaning you will not see the deb simply by list the filesystem.

What I can only say for sure is that the windows exe files are not a problem; they are all supposed to be there in the Programs directory.

Maybe, for some reasons, a Dapper system simply does not allow you to add Edgy CD as a repo; I just don't know.

---

### Post by Ptero-4 on 2007-12-12
The Desktop CD cannot be used for upgrading a previous version. You need the alternate CD to do that since it's the one that works more similar to the breezy and earlier versions installation CDs.

---

