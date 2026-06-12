---
title: "Upgraded server - PHP not working"
date: 2022-08-31
forum: Installation &amp; Upgrades
---

### Post by asai on 2022-08-31
Hi,

I upgraded my server today from 20.04 to 22.04.
Almost all went well, however php i not working.
When I open a php webpage its only showing the code.
Example, phpmyadmin:
```
<?php

declare(strict_types=1);

use PhpMyAdmin\Routing;

if (! defined('ROOT_PATH')) {
    // phpcs:disable PSR1.Files.SideEffects
    define('ROOT_PATH', __DIR__ . DIRECTORY_SEPARATOR);
    // phpcs:enable
}

global $route, $containerBuilder;

require_once ROOT_PATH . 'libraries/common.inc.php';

$dispatcher = Routing::getDispatcher();
Routing::callControllerForRoute($route, $dispatcher, $containerBuilder);
```

What is missing?

---

### Post by asai on 2022-10-04
Haven't solved this issue yet... :(
I have another server that need an upgrade, but I don't risk it yet.

> **asai said:**
> Hi,

I upgraded my server today from 20.04 to 22.04.
Almost all went well, however php i not working.
When I open a php webpage its only showing the code.
Example, phpmyadmin:
```
<?php

declare(strict_types=1);

use PhpMyAdmin\Routing;

if (! defined('ROOT_PATH')) {
    // phpcs:disable PSR1.Files.SideEffects
    define('ROOT_PATH', __DIR__ . DIRECTORY_SEPARATOR);
    // phpcs:enable
}

global $route, $containerBuilder;

require_once ROOT_PATH . 'libraries/common.inc.php';

$dispatcher = Routing::getDispatcher();
Routing::callControllerForRoute($route, $dispatcher, $containerBuilder);
```

What is missing?

---

### Post by SeijiSensei on 2022-10-04
Try "sudo apt install libapache2-mod-php" then restart Apache,

---

