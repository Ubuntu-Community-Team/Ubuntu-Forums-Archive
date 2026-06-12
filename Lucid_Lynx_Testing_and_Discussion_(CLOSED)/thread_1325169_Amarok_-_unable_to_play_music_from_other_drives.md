---
title: "Amarok - unable to play music from other drives"
date: 2009-11-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Kevbert on 2009-11-13
Using Lucid 2.6.32-3 Ubuntu and after the latest pulseaudio updates which gave no sound, I decided to check out Amarok 2.2.0. If I try to add or play a music file that's on a separate drive or partition nothing happens. The track isn't added to the playlist but just sits there. I tried to raise a bug on this via Help-Report bug... but that isn't working either. 
By running Amarok in terminal I get
```
$ amarok
Object::connect: No such signal BrowserCategoryList::leavingTree()
Object::connect:  (sender name:   'internet')
Object::connect: No such signal BrowserCategoryList::leavingTree()
Object::connect:  (sender name:   'root list')
Object::connect: No such slot BrowserWidget::categoryChanged()
Object::connect:  (sender name:   'root list')
QLayout: Attempting to add QLayout "" to Playlist::SortWidget "", which already has a layout
QWidget::insertAction: Attempt to insert null action
QGraphicsLinearLayout::removeAt: invalid index 1
Object::connect: No such signal BrowserWidget::widgetActivated( int )
Object::connect:  (receiver name: 'MainWindow')
Object::connect: No such signal CollectionWidget::home()
Object::connect:  (sender name:   'collections')
Object::connect:  (receiver name: 'root list')
Object::connect: No such signal ServiceBrowser::home()
Object::connect:  (sender name:   'internet')
Object::connect:  (receiver name: 'root list')
Object::connect: No such signal BrowserCategoryList::leavingTree()
Object::connect:  (sender name:   'playlists')
Object::connect: No such signal PlaylistBrowserNS::DynamicCategory::home()
Object::connect:  (receiver name: 'playlists')
"building tree with 0 leafs." 
m_groupHash:  
() 
Object::connect: No such signal PlaylistBrowserNS::PlaylistCategory::home()
Object::connect:  (receiver name: 'playlists')
Object::connect: No such signal PlaylistBrowserNS::PodcastCategory::home()
Object::connect:  (receiver name: 'playlists')
Object::connect: No such signal PlaylistBrowserNS::PlaylistBrowser::home()
Object::connect:  (sender name:   'playlists')
Object::connect:  (receiver name: 'root list')
Object::connect: No such signal FileBrowser::Widget::home()
Object::connect:  (sender name:   'files')
Object::connect:  (receiver name: 'root list')
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x3c00024
amarok:  ********************************************************************************************** 
amarok:  ** AMAROK WAS STARTED IN NORMAL MODE. IF YOU WANT TO SEE DEBUGGING INFORMATION, PLEASE USE: ** 
amarok:  ** amarok --debug                                                                           ** 
amarok:  ********************************************************************************************** 
kevin@kevin-dt1b-LL:~$ Object::connect: No such signal Playlist::GroupingProxy::activeRowChanged( int )
Object::connect:  (sender name:   'GroupingProxy')
Object::connect: No such signal Playlist::GroupingProxy::activeRowChanged( int )
Object::connect:  (sender name:   'GroupingProxy')
Object::connect: No such signal Playlist::GroupingProxy::activeRowChanged( int )
Object::connect:  (sender name:   'GroupingProxy')
```
Drag and drop also does not work.

---

### Post by deadbeef101 on 2010-02-09
I have a very similar problem but in Karmic. No playlist is displayed ( see screenshot).

If this is not the right place to post this, please remove and/or advise

Output when running from terminal:

```
Object::connect: No such signal BrowserCategoryList::leavingTree()
Object::connect:  (sender name:   'internet')
Object::connect: No such signal BrowserCategoryList::leavingTree()
Object::connect:  (sender name:   'root list')
Object::connect: No such slot BrowserWidget::categoryChanged()
Object::connect:  (sender name:   'root list')
QLayout: Attempting to add QLayout "" to Playlist::SortWidget "", which already has a layout
QWidget::insertAction: Attempt to insert null action
Object::connect: No such signal BrowserWidget::widgetActivated( int )
Object::connect:  (receiver name: 'MainWindow')
Object::connect: No such signal CollectionWidget::home()
Object::connect:  (sender name:   'collections')
Object::connect:  (receiver name: 'root list')
Object::connect: No such signal ServiceBrowser::home()
Object::connect:  (sender name:   'internet')
Object::connect:  (receiver name: 'root list')
Object::connect: No such signal BrowserCategoryList::leavingTree()
Object::connect:  (sender name:   'playlists')
Object::connect: No such signal PlaylistBrowserNS::DynamicCategory::home()
Object::connect:  (receiver name: 'playlists')
"building tree with 1 leafs."
QString :  QVariant(QString, "")
QIcon :  QVariant(QIcon, )
QString :  QVariant(QString, "")
QString :  QVariant(QString, "")
m_groupHash:
(0)
Object::connect: No such signal PlaylistBrowserNS::PlaylistCategory::home()
Object::connect:  (receiver name: 'playlists')
Object::connect: No such signal PlaylistBrowserNS::PodcastCategory::home()
Object::connect:  (receiver name: 'playlists')
Object::connect: No such signal PlaylistBrowserNS::PlaylistBrowser::home()
Object::connect:  (sender name:   'playlists')
Object::connect:  (receiver name: 'root list')
Object::connect: No such signal FileBrowser::Widget::home()
Object::connect:  (sender name:   'files')
Object::connect:  (receiver name: 'root list')
amarok:  **********************************************************************************************
amarok:  ** AMAROK WAS STARTED IN NORMAL MODE. IF YOU WANT TO SEE DEBUGGING INFORMATION, PLEASE USE: **
amarok:  ** amarok --debug                                                                           **
amarok:  **********************************************************************************************
jason@odin(--):~$ Object::connect: No such signal Playlist::GroupingProxy::activeRowChanged( int )
Object::connect:  (sender name:   'GroupingProxy')
Object::connect: No such signal Playlist::GroupingProxy::activeRowChanged( int )
Object::connect:  (sender name:   'GroupingProxy')
Object::connect: No such signal Playlist::GroupingProxy::activeRowChanged( int )
Object::connect:  (sender name:   'GroupingProxy')

```

---

### Post by oldsoundguy on 2010-02-09
Try browsing to your files you wish to play.  Highlight and right click then select "open with Amarok"  (mine is set as the preferred player).

I can play audio from a dozen drives spread across 7 networked computers ... 2 running XP and 5 running 4 different Linux platforms without a hitch.

---

### Post by Kevbert on 2010-02-10
That wasn't possible in Lucid Kubuntu. Still had no audio. May try a re-install of Kubuntu later.

---

