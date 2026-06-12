---
title: "Cannot upgrade or get updates -- Help!"
date: 2013-01-24
forum: Installation &amp; Upgrades
---

### Post by Lloyd Cary on 2013-01-24
*****

    
     I have a Linux question I hope you can help me with.   :KS

     
    
     I am currently running _**Ubuntu 10.11**_.  For some time I was running _FrostWire_ and it       stopped working, and so I attempted to remove it.  Shortly after, I       brought up my *Package Manager* and received the following       error       message:  **“The package frostwire needs to be reinstalled but I         can’t find an archive for it.” ** I downloaded Frostwire again,       but it wold not reinstall. Further, I cannot use the package       manager       without the *same* message coming up.
     
    
     I opened a *monitor* to find where there the Frostwire       files       might be located by typing **“locate frostwire”** and the       following l-o-n-g file appeared: [COLOR=#808080][Reproduced below         for your inspection.] [/COLOR]     
     
    
     lloyd@CaryComputer:~$ locate       frostwire     
     /home/lloyd/.frostwire5     
     /home/lloyd/.frostwire5/appwork     
     /home/lloyd/.frostwire5/azureus     
     /home/lloyd/.frostwire5/azureus.lock     
     /home/lloyd/.frostwire5/dbs     
     /home/lloyd/.frostwire5/frostwire.props     
     /home/lloyd/.frostwire5/image_cache     
     /home/lloyd/.frostwire5/installation.props     
     /home/lloyd/.frostwire5/installer.dat     
     /home/lloyd/.frostwire5/intent.props     
     /home/lloyd/.frostwire5/itunes.props     
     /home/lloyd/.frostwire5/jd_home     
     /home/lloyd/.frostwire5/library_db     
     /home/lloyd/.frostwire5/questions.props     
     /home/lloyd/.frostwire5/search_db     
     /home/lloyd/.frostwire5/seenMessages.dat     
     /home/lloyd/.frostwire5/skins.dat     
     /home/lloyd/.frostwire5/tables.props     
     /home/lloyd/.frostwire5/themes     
     /home/lloyd/.frostwire5/updates     
     /home/lloyd/.frostwire5/appwork/cfg     
     /home/lloyd/.frostwire5/appwork/logs     
     /home/lloyd/.frostwire5/appwork/tmp     
     /home/lloyd/.frostwire5/appwork/cfg/org.jdownloader.controlling.filter.LinkFilterSettings.filterlist.json     
     /home/lloyd/.frostwire5/appwork/cfg/org.jdownloader.controlling.packagizer.PackagizerSettings.rulelist.json     
     /home/lloyd/.frostwire5/appwork/cfg/org.jdownloader.settings.AccountSettings.accounts.ejs     
     /home/lloyd/.frostwire5/appwork/cfg/org.jdownloader.settings.InternetConnectionSettings.customproxylist.json     
     /home/lloyd/.frostwire5/appwork/cfg/org.jdownloader.settings.InternetConnectionSettings.directgatewaylist.json     
     /home/lloyd/.frostwire5/appwork/cfg/subconf_AccountController.ejs     
     /home/lloyd/.frostwire5/appwork/cfg/subconf_LOCALE.ejs     
     /home/lloyd/.frostwire5/appwork/cfg/subconf_youtube.com.ejs     
     /home/lloyd/.frostwire5/appwork/logs/2012-10-12.log     
     /home/lloyd/.frostwire5/appwork/logs/2012-10-21.log     
     /home/lloyd/.frostwire5/appwork/logs/2012-4-3.log     
     /home/lloyd/.frostwire5/appwork/tmp/crawler.ejs     
     /home/lloyd/.frostwire5/appwork/tmp/hosts.json     
     /home/lloyd/.frostwire5/azureus/.certs     
     /home/lloyd/.frostwire5/azureus/.keystore     
     /home/lloyd/.frostwire5/azureus/.lock     
     /home/lloyd/.frostwire5/azureus/active     
     /home/lloyd/.frostwire5/azureus/azureus.config     
     /home/lloyd/.frostwire5/azureus/azureus.config.bak     
     /home/lloyd/.frostwire5/azureus/azureus.statistics     
     /home/lloyd/.frostwire5/azureus/azureus.statistics.bak     
     /home/lloyd/.frostwire5/azureus/banips.config     
     /home/lloyd/.frostwire5/azureus/banips.config.bak     
     /home/lloyd/.frostwire5/azureus/dht     
     /home/lloyd/.frostwire5/azureus/downloads.config     
     /home/lloyd/.frostwire5/azureus/downloads.config.bak     
     /home/lloyd/.frostwire5/azureus/ipfilter.cache     
     /home/lloyd/.frostwire5/azureus/logs     
     /home/lloyd/.frostwire5/azureus/net     
     /home/lloyd/.frostwire5/azureus/tmp     
     /home/lloyd/.frostwire5/azureus/active/41BCB3860D5E5D20D3F9DA9FFEF2AEFCF5537EE2.dat     
     /home/lloyd/.frostwire5/azureus/active/41BCB3860D5E5D20D3F9DA9FFEF2AEFCF5537EE2.dat.bak     
     /home/lloyd/.frostwire5/azureus/active/90284019C1A3EAFC6F1377B867FF201CE1EC30AE     
     /home/lloyd/.frostwire5/azureus/active/90284019C1A3EAFC6F1377B867FF201CE1EC30AE.dat     
     /home/lloyd/.frostwire5/azureus/active/90284019C1A3EAFC6F1377B867FF201CE1EC30AE.dat.bak     
     /home/lloyd/.frostwire5/azureus/active/906269E922B95A2A75463C850A0A4AFB6962DCFE.dat     
     /home/lloyd/.frostwire5/azureus/active/906269E922B95A2A75463C850A0A4AFB6962DCFE.dat.bak     
     /home/lloyd/.frostwire5/azureus/active/A2A373492EFC208BF8B44EDC55102FA696441465.dat     
     /home/lloyd/.frostwire5/azureus/active/A2A373492EFC208BF8B44EDC55102FA696441465.dat.bak     
     /home/lloyd/.frostwire5/azureus/active/A9CA94CEF8F8D44F9C1663E4F557AF3B67091C23.dat     
     /home/lloyd/.frostwire5/azureus/active/A9CA94CEF8F8D44F9C1663E4F557AF3B67091C23.dat.bak     
     /home/lloyd/.frostwire5/azureus/active/AFF8D85F66374D4AFA0B8F0A1F02DA2DAE2B9D5F.dat     
     /home/lloyd/.frostwire5/azureus/active/AFF8D85F66374D4AFA0B8F0A1F02DA2DAE2B9D5F.dat.bak     
     /home/lloyd/.frostwire5/azureus/active/C2487EDD4AEB559F058DABE80B28B2C49C62F6A3.dat     
     /home/lloyd/.frostwire5/azureus/active/C2487EDD4AEB559F058DABE80B28B2C49C62F6A3.dat.bak     
     /home/lloyd/.frostwire5/azureus/active/cache.dat     
     /home/lloyd/.frostwire5/azureus/active/90284019C1A3EAFC6F1377B867FF201CE1EC30AE/fmfile104.dat     
     /home/lloyd/.frostwire5/azureus/active/90284019C1A3EAFC6F1377B867FF201CE1EC30AE/fmfile106.dat     
     /home/lloyd/.frostwire5/azureus/active/90284019C1A3EAFC6F1377B867FF201CE1EC30AE/fmfile892.dat     
     /home/lloyd/.frostwire5/azureus/dht/addresses.dat     
     /home/lloyd/.frostwire5/azureus/dht/contacts.dat     
     /home/lloyd/.frostwire5/azureus/dht/diverse.dat     
     /home/lloyd/.frostwire5/azureus/dht/general.dat     
     /home/lloyd/.frostwire5/azureus/dht/version.dat     
     /home/lloyd/.frostwire5/azureus/logs/debug_1.log     
     /home/lloyd/.frostwire5/azureus/logs/debug_2.log     
     /home/lloyd/.frostwire5/azureus/logs/save     
     /home/lloyd/.frostwire5/azureus/net/pm_13638.dat     
     /home/lloyd/.frostwire5/azureus/net/pm_default.dat     
     /home/lloyd/.frostwire5/azureus/tmp/AZU4598336536945715098.tmp     
     /home/lloyd/.frostwire5/azureus/tmp/AZU6101243009441972678.tmp     
     /home/lloyd/.frostwire5/azureus/tmp/AZU8763953221270734530.tmp     
     /home/lloyd/.frostwire5/dbs/sharefiles.1     
     /home/lloyd/.frostwire5/dbs/sharefiles.1/sharefiles.h2.db     
     /home/lloyd/.frostwire5/image_cache/[static.frostwire.com]("http://static.frostwire.com")     
     /home/lloyd/.frostwire5/image_cache/[static.frostwire.com/images]("http://static.frostwire.com/images")     
     /home/lloyd/.frostwire5/image_cache/[static.frostwire.com/images/overlays]("http://static.frostwire.com/images/overlays")     
     /home/lloyd/.frostwire5/image_cache/[static.frostwire.com/images/overlays/Hi_Rez__Lost_Time__overlay_2.jpg]("http://static.frostwire.com/images/overlays/Hi_Rez__Lost_Time__overlay_2.jpg")     
     /home/lloyd/.frostwire5/image_cache/[static.frostwire.com/images/overlays/Illfigga_overlay_new.jpg]("http://static.frostwire.com/images/overlays/Illfigga_overlay_new.jpg")     
     /home/lloyd/.frostwire5/image_cache/[static.frostwire.com/images/overlays/android_market_overlay3.png]("http://static.frostwire.com/images/overlays/android_market_overlay3.png")     
     /home/lloyd/.frostwire5/image_cache/[static.frostwire.com/images/overlays/aucan_black_rainbow_overlay.jpg]("http://static.frostwire.com/images/overlays/aucan_black_rainbow_overlay.jpg")     
     /home/lloyd/.frostwire5/image_cache/[static.frostwire.com/images/overlays/azoora__a_thousand_ways_ep__overlay_v2.jpg]("http://static.frostwire.com/images/overlays/azoora__a_thousand_ways_ep__overlay_v2.jpg")     
     /home/lloyd/.frostwire5/image_cache/[static.frostwire.com/images/overlays/azoora_overlay.jpg]("http://static.frostwire.com/images/overlays/azoora_overlay.jpg")     
     /home/lloyd/.frostwire5/image_cache/[static.frostwire.com/images/overlays/baiyu_fanfair_overlay.jpg]("http://static.frostwire.com/images/overlays/baiyu_fanfair_overlay.jpg")     
     /home/lloyd/.frostwire5/image_cache/[static.frostwire.com/images/overlays/baiyu_overlay.jpg]("http://static.frostwire.com/images/overlays/baiyu_overlay.jpg")     
     /home/lloyd/.frostwire5/image_cache/[static.frostwire.com/images/overlays/carsie_blanton_overlay_new.jpg]("http://static.frostwire.com/images/overlays/carsie_blanton_overlay_new.jpg")     
     /home/lloyd/.frostwire5/image_cache/[static.frostwire.com/images/overlays/cinema_sleep_overlay2.jpg]("http://static.frostwire.com/images/overlays/cinema_sleep_overlay2.jpg")     
     /home/lloyd/.frostwire5/image_cache/[static.frostwire.com/images/overlays/dunson__the_investment__overlay_v2.jpg]("http://static.frostwire.com/images/overlays/dunson__the_investment__overlay_v2.jpg")     
     /home/lloyd/.frostwire5/image_cache/[static.frostwire.com/images/overlays/elemint_brain_food_overlay.jpg]("http://static.frostwire.com/images/overlays/elemint_brain_food_overlay.jpg")     
     /home/lloyd/.frostwire5/image_cache/[static.frostwire.com/images/overlays/farkus_overlay_new.jpg]("http://static.frostwire.com/images/overlays/farkus_overlay_new.jpg")     
     /home/lloyd/.frostwire5/image_cache/[static.frostwire.com/images/overlays/fhernando_ldod_overlay.jpg]("http://static.frostwire.com/images/overlays/fhernando_ldod_overlay.jpg")     
     /home/lloyd/.frostwire5/image_cache/[static.frostwire.com/images/overlays/hi-rez_overlay.jpg]("http://static.frostwire.com/images/overlays/hi-rez_overlay.jpg")     
     /home/lloyd/.frostwire5/image_cache/[static.frostwire.com/images/overlays/jermaine_riley__overlay2.jpg]("http://static.frostwire.com/images/overlays/jermaine_riley__overlay2.jpg")     
     /home/lloyd/.frostwire5/image_cache/[static.frostwire.com/images/overlays/jermaine_riley_bw_overlay_new.jpg]("http://static.frostwire.com/images/overlays/jermaine_riley_bw_overlay_new.jpg")     
     /home/lloyd/.frostwire5/image_cache/[static.frostwire.com/images/overlays/john_graham_success_in_retrograde.jpg]("http://static.frostwire.com/images/overlays/john_graham_success_in_retrograde.jpg")     
     /home/lloyd/.frostwire5/image_cache/[static.frostwire.com/images/overlays/kellee_maize__owl_time__overlay.jpg]("http://static.frostwire.com/images/overlays/kellee_maize__owl_time__overlay.jpg")     
     /home/lloyd/.frostwire5/image_cache/[static.frostwire.com/images/overlays/kellee_maize_integration_overlay.jpg]("http://static.frostwire.com/images/overlays/kellee_maize_integration_overlay.jpg")     
     /home/lloyd/.frostwire5/image_cache/[static.frostwire.com/images/overlays/like_frostwire_overlay.jpg]("http://static.frostwire.com/images/overlays/like_frostwire_overlay.jpg")     
     /home/lloyd/.frostwire5/image_cache/[static.frostwire.com/images/overlays/manter__overlay.jpg]("http://static.frostwire.com/images/overlays/manter__overlay.jpg")     
     /home/lloyd/.frostwire5/image_cache/[static.frostwire.com/images/overlays/no_way_josie_overlay_new.jpg]("http://static.frostwire.com/images/overlays/no_way_josie_overlay_new.jpg")     
     /home/lloyd/.frostwire5/image_cache/[static.frostwire.com/images/overlays/overlay_android_sharing.jpg]("http://static.frostwire.com/images/overlays/overlay_android_sharing.jpg")     
     /home/lloyd/.frostwire5/image_cache/[static.frostwire.com/images/overlays/prosthetik_intelligentz__sounds_and_wonders__overlay.jpg]("http://static.frostwire.com/images/overlays/prosthetik_intelligentz__sounds_and_wonders__overlay.jpg")     
     /home/lloyd/.frostwire5/image_cache/[static.frostwire.com/images/overlays/prosthetik_man_cave_overlay.jpg]("http://static.frostwire.com/images/overlays/prosthetik_man_cave_overlay.jpg")     
     /home/lloyd/.frostwire5/image_cache/[static.frostwire.com/images/overlays/rogue_valley_overlay_new.jpg]("http://static.frostwire.com/images/overlays/rogue_valley_overlay_new.jpg")     
     /home/lloyd/.frostwire5/image_cache/[static.frostwire.com/images/overlays/senor_kaos_overlay2.jpg]("http://static.frostwire.com/images/overlays/senor_kaos_overlay2.jpg")     
     /home/lloyd/.frostwire5/image_cache/[static.frostwire.com/images/overlays/swear_and_shake__maple_ridge__overlay_2.jpg]("http://static.frostwire.com/images/overlays/swear_and_shake__maple_ridge__overlay_2.jpg")     
     /home/lloyd/.frostwire5/image_cache/[static.frostwire.com/images/overlays/sweetheart_overlay.jpg]("http://static.frostwire.com/images/overlays/sweetheart_overlay.jpg")     
     /home/lloyd/.frostwire5/image_cache/[static.frostwire.com/images/overlays/the_sliders_overlay2.jpg]("http://static.frostwire.com/images/overlays/the_sliders_overlay2.jpg")     
     /home/lloyd/.frostwire5/image_cache/[static.frostwire.com/images/overlays/the_ugly_club__you_belong_to_the_minutes__overlay.jpg]("http://static.frostwire.com/images/overlays/the_ugly_club__you_belong_to_the_minutes__overlay.jpg")     
     /home/lloyd/.frostwire5/image_cache/[static.frostwire.com/images/overlays/toussaint_morrison__overlay_2.jpg]("http://static.frostwire.com/images/overlays/toussaint_morrison__overlay_2.jpg")     
     /home/lloyd/.frostwire5/image_cache/[static.frostwire.com/images/overlays/wordsmith_prelude_to_the_king_overlay.jpg]("http://static.frostwire.com/images/overlays/wordsmith_prelude_to_the_king_overlay.jpg")     
     /home/lloyd/.frostwire5/jd_home/JDownloader.log     
     /home/lloyd/.frostwire5/jd_home/JDownloader.log.1     
     /home/lloyd/.frostwire5/library_db/library_db     
     /home/lloyd/.frostwire5/library_db/library_db.h2.db     
     /home/lloyd/.frostwire5/library_db/library_db/segments.gen     
     /home/lloyd/.frostwire5/library_db/library_db/segments_3     
     /home/lloyd/.frostwire5/search_db/search_db.h2.db     
     /home/lloyd/.frostwire5/updates/frostwire-5.3.5.all.deb     
     /home/lloyd/.frostwire5/updates/frostwire-5.3.6.all.deb     
     /home/lloyd/.frostwire5/updates/frostwire-5.3.6.all.deb.torrent     
     /home/lloyd/.frostwire5/updates/frostwire-5.3.7.all.deb     
     /home/lloyd/.frostwire5/updates/frostwire-5.3.7.all.deb.torrent     
     /home/lloyd/.frostwire5/updates/frostwire-5.3.8.all.deb     
     /home/lloyd/.frostwire5/updates/frostwire-5.3.8.all.deb.torrent     
     /home/lloyd/.frostwire5/updates/frostwire-5.3.9.all.deb     
     /home/lloyd/.local/share/Trash/info/frostwire.0.crash.trashinfo     
     /home/lloyd/.local/share/Trash/info/frostwire.1.gz.dpkg-new.trashinfo     
     /home/lloyd/.local/share/Trash/info/frostwire.10.png.dpkg-new.trashinfo     
     /home/lloyd/.local/share/Trash/info/frostwire.11.png.dpkg-new.trashinfo     
     /home/lloyd/.local/share/Trash/info/frostwire.12.png.dpkg-new.trashinfo     
     /home/lloyd/.local/share/Trash/info/frostwire.13.png.dpkg-new.trashinfo     
     /home/lloyd/.local/share/Trash/info/frostwire.14.png.dpkg-new.trashinfo     
     /home/lloyd/.local/share/Trash/info/frostwire.15.png.dpkg-new.trashinfo     
     /home/lloyd/.local/share/Trash/info/frostwire.16.png.dpkg-new.trashinfo     
     /home/lloyd/.local/share/Trash/info/frostwire.17.png.dpkg-new.trashinfo     
     /home/lloyd/.local/share/Trash/info/frostwire.18.png.dpkg-new.trashinfo     
     /home/lloyd/.local/share/Trash/info/frostwire.19.png.dpkg-new.trashinfo     
     /home/lloyd/.local/share/Trash/info/frostwire.2.0.crash.trashinfo     
     /home/lloyd/.local/share/Trash/info/frostwire.2.1.gz.dpkg-new.trashinfo     
     /home/lloyd/.local/share/Trash/info/frostwire.2.desktop.dpkg-new.trashinfo     
     /home/lloyd/.local/share/Trash/info/frostwire.2.png.dpkg-new.trashinfo     
     /home/lloyd/.local/share/Trash/info/frostwire.2.trashinfo     
     /home/lloyd/.local/share/Trash/info/frostwire.20.png.dpkg-new.trashinfo     
     /home/lloyd/.local/share/Trash/info/frostwire.21.png.dpkg-new.trashinfo     
     /home/lloyd/.local/share/Trash/info/frostwire.22.png.dpkg-new.trashinfo     
     /home/lloyd/.local/share/Trash/info/frostwire.23.png.dpkg-new.trashinfo     
     /home/lloyd/.local/share/Trash/info/frostwire.24.png.dpkg-new.trashinfo     
     /home/lloyd/.local/share/Trash/info/frostwire.3.1.gz.dpkg-new.trashinfo     
     /home/lloyd/.local/share/Trash/info/frostwire.3.desktop.dpkg-new.trashinfo     
     /home/lloyd/.local/share/Trash/info/frostwire.3.png.dpkg-new.trashinfo     
     /home/lloyd/.local/share/Trash/info/frostwire.3.trashinfo     
     /home/lloyd/.local/share/Trash/info/frostwire.4.1.gz.dpkg-new.trashinfo     
     /home/lloyd/.local/share/Trash/info/frostwire.4.png.dpkg-new.trashinfo     
     /home/lloyd/.local/share/Trash/info/frostwire.4.trashinfo     
     /home/lloyd/.local/share/Trash/info/frostwire.5.png.dpkg-new.trashinfo     
     /home/lloyd/.local/share/Trash/info/frostwire.5.trashinfo     
     /home/lloyd/.local/share/Trash/info/frostwire.6.png.dpkg-new.trashinfo     
     /home/lloyd/.local/share/Trash/info/frostwire.6.trashinfo     
     /home/lloyd/.local/share/Trash/info/frostwire.7.png.dpkg-new.trashinfo     
     /home/lloyd/.local/share/Trash/info/frostwire.7.trashinfo     
     /home/lloyd/.local/share/Trash/info/frostwire.8.png.dpkg-new.trashinfo     
     /home/lloyd/.local/share/Trash/info/frostwire.8.trashinfo     
     /home/lloyd/.local/share/Trash/info/frostwire.9.png.dpkg-new.trashinfo     
     /home/lloyd/.local/share/Trash/info/frostwire.desktop.dpkg-new.trashinfo     
     /home/lloyd/.local/share/Trash/info/frostwire.png.dpkg-new.trashinfo     
     /home/lloyd/.local/share/Trash/info/frostwire.trashinfo     
     /home/lloyd/Desktop/My       Downloads/frostwire-5.5.2.all(1).deb     
     /home/lloyd/Desktop/My       Downloads/frostwire-5.5.2.all.deb     
     /usr/share/icons/hicolor/256x256/apps/frostwire.png.dpkg-new     
     /usr/share/icons/hicolor/32x32/apps/frostwire.png.dpkg-new     
     /usr/share/icons/hicolor/48x48/apps/frostwire.png.dpkg-new     
     /usr/share/icons/hicolor/64x64/apps/frostwire.png.dpkg-new     
     /usr/share/man/man1/frostwire.1.gz.dpkg-new     
     /var/crash/frostwire.0.crash
      
    
     lloyd@CaryComputer:~$     
     lloyd@CaryComputer:~$     
           lloyd@CaryComputer:~$ 
     
    
     Mysteriously,       my       TRASH bin tells me the trash bin is [I][U]empty!
          
        [/U][/I]
     I attempted to       use the command:


      “**sudo rm -R       -F frostwire**” and:


     “sudo rm -R -F       /usr/share/icons/hicolor/256x256/apps/frostwire.png.dpkg-new       ”       along with several other listings under “**locate**” and *nothing*       worked.
     
      I also tried,       for example, the **rmdir       ** command with no results:


     $ sudo rmdir       /usr/share/man/man1/frostwire.1.gz.dpkg-new     
      [sudo] password for lloyd:


      rmdir: failed to remove       `/usr/share/man/man1/frostwire.1.gz.dpkg-new':   _Not a directory     _
     
      I just keep       getting the same  **“The package frostwire needs to be reinstalled but         I         can’t find an archive for it.”** error message.


     I got a **Ubuntu 12.10** Ubuntu disk       and attempted to **upgrade** the program but it keeps hanging       up       at the “**_Saving installed packages_**” stage.  (I even let it       there overnight!) Thus I cannot upgrade to version 12.10.  Also, I       cannot upgrade from the Synaptic Package Manager.  (I sometimes get       the message: “**Internal error opening cache (1) Please report**,”       followed by the same error message, “ **“The package frostwire         needs to be reinstalled but I can’t find an archive for it.”  I         also cannot update any packages.**
     
      So it seems I       have to get *rid* of the old Frostwire items before I can do       anything else.  But seem unable to do so.  (I even got a second       _Ubuntu       12.10 Studio_ disk in case there may have been something wrong with the       first-- no change.  Same problem. ) *The Computer Janitor* and the *Remove         Orphaned Packages* applicators show *nothing*.

    
     I have been       trying for over *a week*, going on line for help, using       various       commands, using the GNOME Commander, Midnight Commander, etc., and unable to resolve       the       problem.  Perhaps there is some mysterious command line I need to       type       in and cannot find it?  (I am not all that erudite with Linux commands.)



     *I really need help on this one. *Do you have any       ideas or suggestions for a 73-year-old Lenux-retard?
     
      
    
     Thanks for your       time, patience., and expertise.   :D



*****

---

### Post by Bashing-om on 2013-01-24
> I am currently running _**Ubuntu 10.11**_.;Did you mean 11.10 ? 
How did you initially install the frostwire application ?
However method you used to install depends on how to (un)install it.
[INDENT][INDENT]regards
[/INDENT][/INDENT]

---

### Post by Lloyd Cary on 2013-01-25
*****
  Yes, I meant Ubuntu 11.10.

  If memory serves me right, I had originally downloaded Frostwire from its mother-site.  When I attempted to remove it, it did not show up on my Synaptic Package Manager, and since it had stopped working anyway, I tried to uninstall it manually, then tried to reinstall it, which it would not do.*  It seems I did not clear out ALL the Frostwire * *tentacles*, and, as stated in my original post, I can _SEE_ them via the "*locate frostwire*" command, I cannot seem to _delete_them.   Very frustrating.

Thanks for your response.    :D

Lloyd

---

