# Maintainer: Shun Terabayashi <shunonymous@gmail.com>
# Contributor: Zhang Hai <dreaming.in.code.zh@gmail.com>
# Contributor: Vlad M. <vlad@archlinux.net>
# Contributor: Gordin <9ordin @t gmail dot com>
# Contributor: Christoph Bayer <chrbayer@criby.de>

pkgname=android-rebuilds-sdk-platform-tools-bin
pkgver=29.0.6
pkgrel=1
pkgdesc='Platform-Tools for Google Android SDK (adb and fastboot)'
arch=('x86_64')
url='https://android-rebuilds.beuc.net/'
license=('custom')
depends_x86_64=('zlib' 'ncurses')
provides=('adb' 'android-tools')
install="${pkgname}.install"
source=("https://android-rebuilds.beuc.net/dl/repository/sdk-repo-linux-platform-tools-eng.11.0.0_r27.zip"
        "adb.service")
sha1sums=('33fd0f0d45e1030d917c9e3df57e1b4095293bc7'
          '49a40c129199844603afe71fce69c0908e062393')

package() {

  install -Dm644 "${srcdir}/adb.service" "${pkgdir}/usr/lib/systemd/system/adb.service"
  install -Dm644 "${srcdir}/platform-tools/NOTICE.txt" "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"

  install -d "${pkgdir}/etc/profile.d"
  echo 'export PATH="${PATH}:/opt/android-sdk/platform-tools"' >"${pkgdir}/etc/profile.d/${pkgname}.sh"
  echo 'setenv PATH "${PATH}:/opt/android-sdk/platform-tools"' >"${pkgdir}/etc/profile.d/${pkgname}.csh"
  chmod 755 "${pkgdir}/etc/profile.d/${pkgname}".{csh,sh}

  install -d "${pkgdir}/opt/android-sdk/"
  cp -a "${srcdir}/platform-tools" "${pkgdir}/opt/android-sdk/platform-tools"
  chmod -R +rX "${pkgdir}/opt/android-sdk/platform-tools"
}
