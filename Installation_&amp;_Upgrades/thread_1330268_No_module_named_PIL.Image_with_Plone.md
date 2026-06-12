---
title: "No module named PIL.Image with Plone"
date: 2009-11-18
forum: Installation &amp; Upgrades
---

### Post by gatebolduc on 2009-11-18
Hello world,

I just installed an old version of plone (plone2.5) with zope 2.9.3 on my local disk to make some test. Plone and zope work fine, for now. But when i try to import a zexp file i get this error : 'No module named PIL.Image'. But i already install python-image. My python version is 2.4.3.

Thank for helping out, i left the error message, it might help. 

2009-11-18 08:37:50 ERROR ZODB.Connection Couldn't load state for 0x1d39
Traceback (most recent call last):
  File "../Zope-2.9.3/lib/python/ZODB/Connection.py", line 732, in setstate
  File "../Zope-2.9.3/lib/python/ZODB/Connection.py", line 786, in _setstate
  File "../Zope-2.9.3/lib/python/ZODB/serialize.py", line 605, in setGhostState
  File "/home/webconforme/Plone/A2_DESIGN/Zope-2.9.3/instances/MYFIRSTINSTANCE/Products/PortalTransforms/Transform.py", line 109, in __setstate__
    self._tr_init()
  File "/home/webconforme/Plone/A2_DESIGN/Zope-2.9.3/instances/MYFIRSTINSTANCE/Products/PortalTransforms/Transform.py", line 115, in _tr_init
    transform = self._load_transform()
  File "/home/webconforme/Plone/A2_DESIGN/Zope-2.9.3/instances/MYFIRSTINSTANCE/Products/PortalTransforms/Transform.py", line 147, in _load_transform
    m = import_from_name(self.module)
  File "/home/webconforme/Plone/A2_DESIGN/Zope-2.9.3/instances/MYFIRSTINSTANCE/Products/PortalTransforms/Transform.py", line 26, in import_from_name
    m = __import__(module_name)
  File "/home/webconforme/Plone/A2_DESIGN/Zope-2.9.3/instances/MYFIRSTINSTANCE/Products/PortalTransforms/transforms/image_to_png.py", line 1, in ?
    from Products.PortalTransforms.libtransforms.piltransform import PILTransforms
  File "/home/webconforme/Plone/A2_DESIGN/Zope-2.9.3/instances/MYFIRSTINSTANCE/Products/PortalTransforms/libtransforms/piltransform.py", line 3, in ?
    import PIL.Image
ImportError: No module named PIL.Image
2009-11-18 08:37:50 ERROR Zope.SiteErrorLog [http://localhost:8080/manage_importObject](http://localhost:8080/manage_importObject)
Traceback (innermost last):
  Module ZPublisher.Publish, line 115, in publish
  Module ZPublisher.mapply, line 88, in mapply
  Module ZPublisher.Publish, line 41, in call_object
  Module OFS.ObjectManager, line 585, in manage_importObject
  Module OFS.ObjectManager, line 607, in _importObjectFromFile
  Module OFS.ObjectManager, line 330, in _setObject
  Module zope.event, line 23, in notify
  Module zope.app.event.dispatching, line 66, in dispatch
  Module zope.component, line 181, in subscribers
  Module zope.component.site, line 89, in subscribers
  Module zope.interface.adapter, line 481, in subscribers
  Module zope.app.event.objectevent, line 192, in objectEventNotify
  Module zope.component, line 181, in subscribers
  Module zope.component.site, line 89, in subscribers
  Module zope.interface.adapter, line 481, in subscribers
  Module OFS.subscribers, line 117, in dispatchObjectMovedEvent
  Module zope.app.container.contained, line 184, in dispatchToSublocations
  Module zope.component, line 181, in subscribers
  Module zope.component.site, line 89, in subscribers
  Module zope.interface.adapter, line 481, in subscribers
  Module OFS.subscribers, line 117, in dispatchObjectMovedEvent
  Module zope.app.container.contained, line 184, in dispatchToSublocations
  Module zope.component, line 181, in subscribers
  Module zope.component.site, line 89, in subscribers
  Module zope.interface.adapter, line 481, in subscribers
  Module OFS.subscribers, line 114, in dispatchObjectMovedEvent
  Module OFS.subscribers, line 134, in callManageAfterAdd
  Module ZODB.Connection, line 732, in setstate
  Module ZODB.Connection, line 786, in _setstate
  Module ZODB.serialize, line 605, in setGhostState
  Module Products.PortalTransforms.Transform, line 109, in __setstate__
  Module Products.PortalTransforms.Transform, line 115, in _tr_init
   - __traceback_info__: ('Products.PortalTransforms.transforms.image_to_png',)
  Module Products.PortalTransforms.Transform, line 147, in _load_transform
  Module Products.PortalTransforms.Transform, line 26, in import_from_name
   - __traceback_info__: ('Products.PortalTransforms.transforms.image_to_png',)
  Module None, line 1, in ?
  Module None, line 3, in ?
ImportError: No module named PIL.Image

---

