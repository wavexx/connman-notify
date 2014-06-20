connman-notify: desktop notification integration for connman
============================================================

`connman-notify` generates desktop notifications for connman_ events, such as
interface connection/disconnection.

The generated notifications look like::

  ethernet: online [IPv4: 10.1.0.5]
  ethernet: disconnected
  wifi/SSID: configuring ...
  wifi/SSID: online [IPv4: 192.168.0.1]
  ...


Usage
-----

Simply run `connman-notify` at the start of your session:

  ./connman-notify &

Use `connman-notify -h` to see a minimal help. The command line flags `-n` and
`-l` can be used to customize the detail level of the notification (to hide
IPv4/6 addresses or show long `connman` interface names).

You'll need `connman` to be running of course, and you'll also need a
notification daemon such as dunst_.


Why connman
-----------

I'm only interested in DE-agnostic network managers, and `connman` is one of
the few available along with `WICD`, `netcfg` and `dhcpcd`. If you're looking
for a zero-configuration manager, just use `WICD`. `connman` is not "user
friendly" yet.

connman_ however blows `WICD` out of the water in terms of speed. It can bring
my ethernet link up in 2 seconds (compared to ~10 of `WICD`) and perform an
ethernet<=>WiFi switch in generally less than 3 seconds (`WICD` would normally
just fail to reconnect!). Not to mention minimal CPU/memory usage, and good
support for IPv6.

`connman` has no graphical management interface yet. connman-ui_ runs in the
system tray (if you have one), but it's still far away to being complete.

connman_dmenu_ provides a simple dmenu-based WiFi network selector. For a tiled
window-manager setup, the combination of `connman-notify` and `connman_dmenu`
serves my current purposes nicely.


Dependencies
------------

The following software is currently required for `facedetect`:

- Python
- Pynotify (``python-notify``)
- Python DBUS (``python-dbus``)

On Debian/Ubuntu, you can install all the required dependencies with::

  sudo apt-get install python python-notify python-dbus


Authors and Copyright
---------------------

| `connman-notify` is distributed under GPL2 (see COPYING) WITHOUT ANY WARRANTY.
| Copyright(c) 2014 by wave++ "Yuri D'Elia" <wavexx@thregr.org>.

.. _connman: https://01.org/connman
.. _connman-ui: https://github.com/tbursztyka/connman-ui
.. _dunst: http://www.knopwob.org/dunst/
.. _connman_dmenu: https://github.com/taylorchu/connman_dmenu
