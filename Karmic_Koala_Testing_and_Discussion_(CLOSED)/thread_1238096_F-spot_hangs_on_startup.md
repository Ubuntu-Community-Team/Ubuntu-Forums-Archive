---
title: "F-spot hangs on startup"
date: 2009-08-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by hounden on 2009-08-12
Does anyone experience that f-spot hangs on startup? This started after the latest upgrade 11. Aug 2009. 

running f-spot --debug results in the following:


** Running f-spot in Debug Mode **
** Running Mono with --debug   **
[Info  10:40:46.828] Initializing DBus
[Debug 10:40:47.080] DBusInitialization took 0.202687s
[Info  10:40:47.081] Initializing Mono.Addins
[Debug 10:40:47.364] Mono.Addins Initialization took 0.283718s
[Info  10:40:47.387] Starting new FSpot server (f-spot 0.6.0.0)
[Debug 10:40:47.643] Db Initialization took 0.084643s
[Debug 10:40:48.036] Query Started : SELECT * FROM photos  WHERE  photos.id NOT IN (SELECT photo_id FROM photo_tags WHERE tag_id = 2) ORDER BY  time DESC, filename DESC 
[Debug 10:40:48.039] QueryToTemp took 0.003643s : SELECT * FROM photos  WHERE  photos.id NOT IN (SELECT photo_id FROM photo_tags WHERE tag_id = 2) ORDER BY  time DESC, filename DESC 
[Debug 10:40:48.040] Reloading the query took 0.007442s
[Debug 10:40:48.296] PhotosPerMonth took 0.012642s
[Debug 10:40:48.299] TimeAdaptor REAL Reload took 0.22869s
[Debug 10:40:48.394] Query took 0.0299s : SELECT * FROM photoquery_temp_0 LIMIT 100 OFFSET 0
[Debug 10:40:48.495] Query Started : SELECT * FROM photos  WHERE  photos.id NOT IN (SELECT photo_id FROM photo_tags WHERE tag_id = 2) ORDER BY  time DESC, filename DESC 
[Debug 10:40:48.498] QueryToTemp took 0.003128s : SELECT * FROM photos  WHERE  photos.id NOT IN (SELECT photo_id FROM photo_tags WHERE tag_id = 2) ORDER BY  time DESC, filename DESC 
[Debug 10:40:48.517] Query took 0.001014s : SELECT * FROM photoquery_temp_0 LIMIT 100 OFFSET 0
[Debug 10:40:48.597] open uri = file:///home/janne/Photos/2009/08/10/IMG_3677.tif
[Debug 10:40:48.633] open uri = file:///home/janne/Photos/2009/08/10/IMG_3677.tif
[Debug 10:40:48.647] Reloading the query took 0.152358s
[Debug 10:40:48.695] Query Started : SELECT * FROM photos  WHERE  photos.id NOT IN (SELECT photo_id FROM photo_tags WHERE tag_id = 2) ORDER BY  time DESC, filename DESC 
[Debug 10:40:48.698] QueryToTemp took 0.00316s : SELECT * FROM photos  WHERE  photos.id NOT IN (SELECT photo_id FROM photo_tags WHERE tag_id = 2) ORDER BY  time DESC, filename DESC 
[Debug 10:40:48.701] IndexOf took 0.000166s : SELECT ROWID AS row_id FROM photoquery_temp_0 WHERE id = 126
[Debug 10:40:48.701] Reloading the query took 0.006348s
[Debug 10:40:48.714] PhotosPerMonth took 0.009377s
[Debug 10:40:48.714] TimeAdaptor REAL Reload took 0.015611s
[Info  10:40:48.721] Starting BeagleService
[Debug 10:40:48.722] BeagleService startup took 1.7E-05s
[Info  10:40:48.791] Hack for gnome-settings-daemon engaged
[Debug 10:40:48.906] PhotosPerMonth took 0.007578s
[Debug 10:40:48.907] TimeAdaptor REAL Reload took 0.208225s


So any input regarding this? Any fixes or bug reports?

---

