---
title: "how do I move my mail to my new computer?"
date: 2008-11-18
forum: Installation &amp; Upgrades
---

### Post by AlmaTlust on 2008-11-18
I will get a new laptop soon and want to put Kubuntu 8.10 on it. How do I migrate my emails (I'm using kmail)? Everything else shouldn't be a problem...

---

### Post by Odur on 2008-11-18
Backup ~/.kde/share/apps/mail.
After 8.10 install, open KMail and choose import and select your backuped folder. The mail will be imported into a separete folder inside KMail. You can move it to your inbox or another folder after the import.
Note: Only the mails will be imported, not the settings. This only work on maildirs, not on mbox.

---

### Post by ecowan on 2010-10-13
*WARNING*

I had Kubuntu 9.04 & Kmail on a laptop. I bought a new laptop on which I did a clean install of Kubuntu 10.04 and Kontact.

I managed to migrate my ~/* files, my Firefox bookmarks and saved passwords, my kaddressbook by copying various files to a USB stick.
But when it came to importing my email only some folders were copied.

*No error message was issued*.

It turns out Kmail Import doesn't like a USB stick formatted for vfat. When I reformatted it as ext4 and copied ~/.kde/share/apps/kmail/mail to it the new Kontact Kmail Import function brought everything over.

Finally. - erny

---

### Post by rue1341 on 2011-02-17
Here are 2 scripts which I found and have changed so that they work on Kubuntu 10.10. I nearly reverted back to evolution but this seems to work well for me as there is no hunting for files or forgetting any. So thanks to the original code maker . Not sure if this works other than on Kubuntu 10.10 but it does list all the folders required to copy to have all the settings etc in Kontact. to transfer you would copy the tarball onto you new computer.

The script to backup Kontact is:-

```
#/bin/sh                                                                  
# kdepim backup script with kdialog                                       
# v .2 2011-02-13                                                         
#                                                                         

kdialog --msgbox  "TO BACKUP KONTACT CLICK 'OK'
AND CHOOSE THE TARGET FOLDER.
This is a simple backup script for all data related to kdepim and kdenetwork like mails, contacts, settings et cetera. It will save all settings and data for the following apps: akregator, basket, kaddressbook, kgpg, kmail, knotes, kopete, korganizer and kwallet. Just choose the target folder :)"                                                                                                



#
# SETUP
#      

StoreFLDR=$(kdialog --getexistingdirectory ~/ --title " Where shall I store the backup ? ")

        case $? in 
                1) kdialog --sorry "Bye bye" ; exit ;;
                0) mkdir -p $StoreFLDR ; echo "ok" ;; 
        esac                                          

TempFLDR=~/.kontact_backup

        if [ -d "$TempFLDR" ] ; then
                rm -rf $TempFLDR    
                mkdir $TempFLDR     
        else                        
                mkdir $TempFLDR     
        fi                          



#
# DATE FORMAT
#            
# (YY.MM.DD - german) 
#Date=$(date +%d.%m.%g)
# (DD-MM-YY)           

Date=$(date +%g-%m-%d-%H-%M)



#
# LETS START
          dcopRef=$(kdialog --title "Kontact Backup" --progressbar "Initializing . . ." 28)
echo $dcopRef
qdbus $dcopRef org.freedesktop.DBus.Properties.Set org.kde.kdialog.ProgressDialog maximum 28

qdbus $dcopRef org.freedesktop.DBus.Properties.Set org.kde.kdialog.ProgressDialog value 1
qdbus $dcopRef org.kde.kdialog.ProgressDialog.setLabelText "kontact_backup"
                #dcopRef=`kdialog --title "pimBackup" --progressbar "Starting backup ..." 25`
qdbus $dcopRef org.freedesktop.DBus.Properties.Set org.kde.kdialog.ProgressDialog value 2
qdbus $dcopRef org.kde.kdialog.ProgressDialog.setLabelText "Creating temporary folders ..."
               # dcop $dcopRef setProgress 2
                #dcop $dcopRef setLabel "Creating temporary folders ..."
                mkdir $TempFLDR/.kde                                   
                mkdir $TempFLDR/.kde/share                             
                mkdir $TempFLDR/.kde/share/config                      
                mkdir $TempFLDR/.kde/share/apps                        
                mkdir $TempFLDR/.kde/share/config/kresources           
                mkdir $TempFLDR/.gnupg                                 

qdbus $dcopRef org.freedesktop.DBus.Properties.Set org.kde.kdialog.ProgressDialog value 3
qdbus $dcopRef org.kde.kdialog.ProgressDialog.setLabelText "Copying email accounts ..."
                #dcop $dcopRef setProgress 3
                #dcop $dcopRef setLabel "Copying email accounts ..."
                cp $HOME/.kde/share/config/emaildefaults $TempFLDR/.kde/share/config/
qdbus $dcopRef org.freedesktop.DBus.Properties.Set org.kde.kdialog.ProgressDialog value 4
qdbus $dcopRef org.kde.kdialog.ProgressDialog.setLabelText "Copying email identities ..."
               # dcop $dcopRef setProgress 4
                #dcop $dcopRef setLabel "Copying email identities ..."
                cp $HOME/.kde/share/config/emailidentities $TempFLDR/.kde/share/config/

qdbus $dcopRef org.freedesktop.DBus.Properties.Set org.kde.kdialog.ProgressDialog value 5
qdbus $dcopRef org.kde.kdialog.ProgressDialog.setLabelText "Copying kmail settings ..."
                #dcop $dcopRef setProgress 5
               # dcop $dcopRef setLabel "Copying kmail settings ..."
                
                cp $HOME/.kde/share/config/kmailrc $TempFLDR/.kde/share/config/       

qdbus $dcopRef org.freedesktop.DBus.Properties.Set org.kde.kdialog.ProgressDialog value 6
qdbus $dcopRef org.kde.kdialog.ProgressDialog.setLabelText "Copying kaddressbook settings ..."
                #dcop $dcopRef setProgress 6
               # dcop $dcopRef setLabel "Copying kaddressbook settings ..."
                cp $HOME/.kde/share/config/kaddressbookrc $TempFLDR/.kde/share/config/
                cp -r $HOME/.kde/share/config/kresources/contact $TempFLDR/.kde/share/config/kresources/

qdbus $dcopRef org.freedesktop.DBus.Properties.Set org.kde.kdialog.ProgressDialog value 7
qdbus $dcopRef org.kde.kdialog.ProgressDialog.setLabelText "Copying emails and account data ..."
                #dcop $dcopRef setProgress 7
                #dcop $dcopRef setLabel "Copying emails and account data ..."
                cp -r $HOME/.kde/share/apps/kmail $TempFLDR/.kde/share/apps/

qdbus $dcopRef org.freedesktop.DBus.Properties.Set org.kde.kdialog.ProgressDialog value 8
qdbus $dcopRef org.kde.kdialog.ProgressDialog.setLabelText "Copying addressbook ..."
                #dcop $dcopRef setProgress 8
                #dcop $dcopRef setLabel "Copying addressbook ..."
                cp -r $HOME/.kde/share/apps/kabc $TempFLDR/.kde/share/apps/

qdbus $dcopRef org.freedesktop.DBus.Properties.Set org.kde.kdialog.ProgressDialog value 9
qdbus $dcopRef org.kde.kdialog.ProgressDialog.setLabelText "Copying Korganizer settings and entries ..."
                #dcop $dcopRef setProgress 9
                #dcop $dcopRef setLabel "Copying Korganizer settings and entries ..."
                cp $HOME/.kde/share/config/korgacrc $TempFLDR/.kde/share/config/    
                cp $HOME/.kde/share/config/korganizerrc $TempFLDR/.kde/share/config/
                cp -r $HOME/.kde/share/apps/korganizer $TempFLDR/.kde/share/apps/   

qdbus $dcopRef org.freedesktop.DBus.Properties.Set org.kde.kdialog.ProgressDialog value 10
qdbus $dcopRef org.kde.kdialog.ProgressDialog.setLabelText "Copying Kopete settings ..."
                #dcop $dcopRef setProgress 10
                #dcop $dcopRef setLabel "Copying Kopete settings ..."
                cp $HOME/.kde/share/config/kopeterc $TempFLDR/.kde/share/config/
                cp $HOME/.kde/share/config/kopete $TempFLDR/.kde/share/config/  
                cp $HOME/.kde/share/config/kopete.eventsrc $TempFLDR/.kde/share/config/
                cp -r $HOME/.kde/share/apps/kopete $TempFLDR/.kde/share/apps/          
                cp -r $HOME/.kde/share/apps/kopete_otr $TempFLDR/.kde/share/apps/      
                cp -r $HOME/.kde/share/apps/kopeterichtexteditpart $TempFLDR/.kde/share/apps/

qdbus $dcopRef org.freedesktop.DBus.Properties.Set org.kde.kdialog.ProgressDialog value 11
qdbus $dcopRef org.kde.kdialog.ProgressDialog.setLabelText "Copying Konversation settings ..."
                #dcop $dcopRef setProgress 11
                #dcop $dcopRef setLabel "Copying Konversation settings ..."
                cp $HOME/.kde/share/config/konversationrc $TempFLDR/.kde/share/config/
                cp $HOME/.kde/share/config/konversation.eventsrc $TempFLDR/.kde/share/config/
                cp -r $HOME/.kde/share/apps/konversation $TempFLDR/.kde/share/apps/          

qdbus $dcopRef org.freedesktop.DBus.Properties.Set org.kde.kdialog.ProgressDialog value 12
qdbus $dcopRef org.kde.kdialog.ProgressDialog.setLabelText "Copying Knotes settings and notes ..."
                #dcop $dcopRef setProgress 12
                #dcop $dcopRef setLabel "Copying Knotes settings and notes ..."
                cp $HOME/.kde/share/config/knotesrc $TempFLDR/.kde/share/config/
                cp -r $HOME/.kde/share/apps/knotes $TempFLDR/.kde/share/apps/   

qdbus $dcopRef org.freedesktop.DBus.Properties.Set org.kde.kdialog.ProgressDialog value 13
qdbus $dcopRef org.kde.kdialog.ProgressDialog.setLabelText "Copying GPG settings and keys ..."
                #dcop $dcopRef setProgress 13
                #dcop $dcopRef setLabel "Copying GPG settings and keys ..."
                cp $HOME/.kde/share/config/kgpgrc $TempFLDR/.kde/share/config/
                cp -r $HOME/.gnupg/* $TempFLDR/.gnupg/                        

qdbus $dcopRef org.freedesktop.DBus.Properties.Set org.kde.kdialog.ProgressDialog value 14
qdbus $dcopRef org.kde.kdialog.ProgressDialog.setLabelText "Copying Kwallet settings ..."
                #dcop $dcopRef setProgress 13
                #dcop $dcopRef setLabel "Copying Kwallet settings ..."
                cp -r $HOME/.kde/share/apps/kwallet $TempFLDR/.kde/share/apps/
                cp $HOME/.kde/share/config/kwalletrc $TempFLDR/.kde/share/config/

qdbus $dcopRef org.freedesktop.DBus.Properties.Set org.kde.kdialog.ProgressDialog value 15
qdbus $dcopRef org.kde.kdialog.ProgressDialog.setLabelText "Copying Akregator settings ..."
                #dcop $dcopRef setProgress 14
                #dcop $dcopRef setLabel "Copying Akregator settings ..."
                cp $HOME/.kde/share/config/akregator.eventsrc $TempFLDR/.kde/share/config/
                cp $HOME/.kde/share/config/akregatorrc $TempFLDR/.kde/share/config/       
                cp $HOME/.kde/share/config/kopete.eventsrc $TempFLDR/.kde/share/config/   

qdbus $dcopRef org.freedesktop.DBus.Properties.Set org.kde.kdialog.ProgressDialog value 16
qdbus $dcopRef org.kde.kdialog.ProgressDialog.setLabelText "Copying Akregator feeds and cache ..."
                #dcop $dcopRef setProgress 15
                #dcop $dcopRef setLabel "Copying Akregator feeds and cache ..."
                cp -r $HOME/.kde/share/apps/akregator $TempFLDR/.kde/share/apps/

qdbus $dcopRef org.freedesktop.DBus.Properties.Set org.kde.kdialog.ProgressDialog value 17
qdbus $dcopRef org.kde.kdialog.ProgressDialog.setLabelText "Copying Basket settings ..."
                #dcop $dcopRef setProgress 16
                #dcop $dcopRef setLabel "Copying Basket settings ..."
                cp $HOME/.kde/share/config/basketrc $TempFLDR/.kde/share/config/

qdbus $dcopRef org.freedesktop.DBus.Properties.Set org.kde.kdialog.ProgressDialog value 18
qdbus $dcopRef org.kde.kdialog.ProgressDialog.setLabelText "Copying Basket notes ..."
                #dcop $dcopRef setProgress 17
                #dcop $dcopRef setLabel "Copying Basket notes ..."
                cp -r $HOME/.kde/share/apps/basket $TempFLDR/.kde/share/apps/

qdbus $dcopRef org.freedesktop.DBus.Properties.Set org.kde.kdialog.ProgressDialog value 19
qdbus $dcopRef org.kde.kdialog.ProgressDialog.setLabelText "Creating tarball ..."
                #dcop $dcopRef setProgress 18
                #dcop $dcopRef setLabel "Creating tarball ..."
                cd $TempFLDR                                 
                sleep 1                                      

qdbus $dcopRef org.freedesktop.DBus.Properties.Set org.kde.kdialog.ProgressDialog value 20
qdbus $dcopRef org.kde.kdialog.ProgressDialog.setLabelText "Creating tarball ..."
                #dcop $dcopRef setProgress 19
                #dcop $dcopRef setLabel "Creating tarball ..."
                tar cf kontact_backup.tar .                       

qdbus $dcopRef org.freedesktop.DBus.Properties.Set org.kde.kdialog.ProgressDialog value 21
qdbus $dcopRef org.kde.kdialog.ProgressDialog.setLabelText "Checking bzip2 ..."
                #dcop $dcopRef setProgress 20
                #dcop $dcopRef setLabel "Checking bzip2 ..."

                if [ -e "/usr/bin/pbzip2" ] ; then

qdbus $dcopRef org.freedesktop.DBus.Properties.Set org.kde.kdialog.ProgressDialog value 22
qdbus $dcopRef org.kde.kdialog.ProgressDialog.setLabelText "Nice, you have pbzip2 installed :) ..."
                        #dcop $dcopRef setProgress 21
                        #dcop $dcopRef setLabel "Nice, you have pbzip2 installed :) ..."
                        sleep 2 

qdbus $dcopRef org.freedesktop.DBus.Properties.Set org.kde.kdialog.ProgressDialog value 23
qdbus $dcopRef org.kde.kdialog.ProgressDialog.setLabelText "Compressing tarball ..."                                                       
                        #dcop $dcopRef setProgress 22                                   
                       # dcop $dcopRef setLabel "Compressing tarball ..."               
                        pbzip2 -p2 -r kontact_backup.tar                                    
                else     

qdbus $dcopRef org.freedesktop.DBus.Properties.Set org.kde.kdialog.ProgressDialog value 24
qdbus $dcopRef org.kde.kdialog.ProgressDialog.setLabelText "Using standard bzip2 ..."                                                              
                        #dcop $dcopRef setProgress 21                                   
                        #dcop $dcopRef setLabel "Using standard bzip2 ..."              
                        sleep 2  

qdbus $dcopRef org.freedesktop.DBus.Properties.Set org.kde.kdialog.ProgressDialog value 25
qdbus $dcopRef org.kde.kdialog.ProgressDialog.setLabelText "Compressing tarball ..."                                                      
                        #dcop $dcopRef setProgress 22                                   
                        #dcop $dcopRef setLabel "Compressing tarball ..."               
                        bzip2 --best kontact_backup.tar                                     
                fi

qdbus $dcopRef org.freedesktop.DBus.Properties.Set org.kde.kdialog.ProgressDialog value 26
qdbus $dcopRef org.kde.kdialog.ProgressDialog.setLabelText "Moving backup to destination ..."
                #dcop $dcopRef setProgress 23
               # dcop $dcopRef setLabel "Moving backup to destination ..."
                mv kontact_backup.tar.bz2 $StoreFLDR/kontact_backup.$Date.tar.bz2

qdbus $dcopRef org.freedesktop.DBus.Properties.Set org.kde.kdialog.ProgressDialog value 27
qdbus $dcopRef org.kde.kdialog.ProgressDialog.setLabelText "Cleaning up ..."
                #dcop $dcopRef setProgress 24
                #dcop $dcopRef setLabel "Cleaning up ..."
                rm -rf $TempFLDR

qdbus $dcopRef org.freedesktop.DBus.Properties.Set org.kde.kdialog.ProgressDialog value 28
qdbus $dcopRef org.kde.kdialog.ProgressDialog.setLabelText "Backup saved in $StoreFLDR"
                #dcop $dcopRef setProgress 25
                #dcop $dcopRef setLabel "Backup saved in $StoreFLDR"
                sleep 2
                #dcop $dcopRef close
qdbus $dcopRef org.kde.kdialog.ProgressDialog.close

                kdialog --dontagain kontact_backup:alldone --msgbox "You can find the compressed backup in $StoreFLDR, just extract it into your home directory to restore a backup or use the pimRestore script."

                exit 1
```

The script to restore the backup is:-

```
#/bin/sh                                                  
#                                                         
# KMail & Kontact-Restore                                
# Version 2011-02-17                                      
#                                                         


kdialog --title "DCOP Progress" --warningcontinuecancel "WARNING.
ALL UNSAVED DATA WILL BE LOST IF YOU CONTINUE. 
Kontact will be shutdown without anything being saved if you continue. CANCEL this if you need to save any work and run this restore script again."
if [ $? = 0 ]; then
           kill `pgrep kontact`
  else
          kdialog --sorry "Bye bye" ; exit ;
   fi
#
# SETUP
#      
FILE=$(kdialog --getopenfilename ~/ --title "Choose your compressed backup")
case $? in                                                                  
        1) kdialog --sorry "Bye bye" ; exit ;;                              
        0) echo "ok" ;;                                                     
esac                                                                        

TEMPFLDR=~/.pimbackup


#-------------------------------------------------
# START DES SCRIPTS                               
#-------------------------------------------------

                ###
                ### Wiederherstellung starten
                ###                          

                ###
                ### DCOP Interface aktivieren
                ###                          
                dcopRef=`kdialog --title "Restoring Kontact backup" --progressbar "Starting restore" 6`
echo $dcopRef
qdbus $dcopRef org.freedesktop.DBus.Properties.Set org.kde.kdialog.ProgressDialog maximum 6

                ###
                ### Sicherung nach $HOME kopieren
                ###
qdbus $dcopRef org.freedesktop.DBus.Properties.Set org.kde.kdialog.ProgressDialog value 1
qdbus $dcopRef org.kde.kdialog.ProgressDialog.setLabelText "Preparing ..."              
                #dcop $dcopRef setProgress 1      
               # dcop $dcopRef setLabel "Preparing ..."
                mkdir $TEMPFLDR                       
                cp -v $FILE $TEMPFLDR/pimbackup.tar.bz2

                ###
                ### Wechsle nach $HOME
                ###  
qdbus $dcopRef org.freedesktop.DBus.Properties.Set org.kde.kdialog.ProgressDialog value 2
qdbus $dcopRef org.kde.kdialog.ProgressDialog.setLabelText "Preparing ..."                 
                #dcop $dcopRef setProgress 2
                #dcop $dcopRef setLabel "Preparing ..."
                cd $TEMPFLDR                          

                ###
                ### Sicherung entpacken
                ###         
qdbus $dcopRef org.freedesktop.DBus.Properties.Set org.kde.kdialog.ProgressDialog value 3
qdbus $dcopRef org.kde.kdialog.ProgressDialog.setLabelText "Unpacking archive ..."           
                #dcop $dcopRef setProgress 3
                #dcop $dcopRef setLabel "Restoring backup ..."
                tar -xvf pimbackup.tar.bz2                  

qdbus $dcopRef org.freedesktop.DBus.Properties.Set org.kde.kdialog.ProgressDialog value 4
qdbus $dcopRef org.kde.kdialog.ProgressDialog.setLabelText "Restoring files ..."
                #dcop $dcopRef setProgress 4
               # dcop $dcopRef setLabel "Restoring backup ..."
                cp -f -v -R .kde .gnupg $HOME

                ###
                ### Tempor&#65533;e Daten löschen
                ###
qdbus $dcopRef org.freedesktop.DBus.Properties.Set org.kde.kdialog.ProgressDialog value 5
qdbus $dcopRef org.kde.kdialog.ProgressDialog.setLabelText "Cleaning up ..."
                #dcop $dcopRef setProgress 5
                #dcop $dcopRef setLabel "Cleaning up ..."
                rm -rf $TEMPFLDR

                ###
                ### Fertig / DCOP beenden
                ###
qdbus $dcopRef org.freedesktop.DBus.Properties.Set org.kde.kdialog.ProgressDialog value 6
qdbus $dcopRef org.kde.kdialog.ProgressDialog.setLabelText "Done. Bye bye!"
                #dcop $dcopRef setProgress 6
                #dcop $dcopRef setLabel "Done. Bye bye!"
                sleep 5
                #dcop $dcopRef close
qdbus $dcopRef org.kde.kdialog.ProgressDialog.close

                exit 1
```


you will have to set the permission on each script so that it will work. Navigate in the terminal to the folder where you have save the script and run:-

```
chmod 755 nameofscript
```

this should make it work.

If you use a number of scripts you may want to make a new folder called "bin" in the home directory and then you will be able to use a short cut "Alt+F2" to bring up the run dialog. all you need do is type the script's name and run it from there.

---

