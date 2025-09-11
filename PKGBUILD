# SPDX-License-Identifier: AGPL-3.0

#    ----------------------------------------------------------------------
#    Copyright © 2025  Pellegrino Prevete
#
#    All rights reserved
#    ----------------------------------------------------------------------
#
#    This program is free software: you can redistribute it and/or modify
#    it under the terms of the GNU Affero General Public License as published by
#    the Free Software Foundation, either version 3 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU Affero General Public License for more details.
#
#    You should have received a copy of the GNU Affero General Public License
#    along with this program.  If not, see <https://www.gnu.org/licenses/>.

# Maintainer:
#   Truocolo
#     <truocolo@aol.com>
#     <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
# Maintainer:
#   Pellegrino Prevete (dvorak)
#     <pellegrinoprevete@gmail.com>
#     <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>

_evmfs_available="$( \
  command \
    -v \
    "evmfs" || \
    true)"
if [[ ! -v "_evmfs" ]]; then
  if [[ "${_evmfs_available}" != "" ]]; then
    _evmfs="true"
  elif [[ "${_evmfs_available}" == "" ]]; then
    _evmfs="false"
  fi
fi
_os="$( \
  uname \
    -o)"
_arch="$( \
  uname \
    -m)"
_evmfs="true"
_pkg=mame
_pkg_retroarch="${_pkg}arcade"
_pkgname="libretro-${_pkg}"
_Pkg="MAME"
pkgname="${_pkgname}-bin"
pkgver="3.6.1"
pkgrel=1
_pkgdesc=(
  "RetroArch backend for"
  "the MAME multi-purpose"
  "emulation framework."
)
pkgdesc="${_pkgdesc[*]}"
arch=(
  'aarch64'
  'arm'
  'armv7l'
)
_http="https://github.com"
_ns="libretro"
url="${_http}/${_ns}/${_pkg}"
license=(
  'GPL2'
)
depends=(
  'retroarch'
)
if [[ "${_os}" != "GNU/Linux" ]] && \
   [[ "${_os}" == "Android" ]]; then
  depends+=(
    'inteppacman'
  )
fi
optdepends=(
)
[[ "${_os}" != "GNU/Linux" ]] && \
[[ "${_os}" == "Android" ]] && \
  optdepends+=(
  )
makedepends=(
  'coreutils'
  'evmfs'
)
checkdepends=(
)
provides=(
  "${_pkg}=${pkgver}"
  "${_pkg_retroarch}"
  "${_pkgname}=${pkgver}"
)
conflicts=(
  "${_pkgname}"
)
source=()
sha256sums=()
_lib_aarch64_sum="b2176ab27df1a92201364b5317d6f514cd56a3c939499f444aee86415a5bdf4f"
_lib_aarch64_sig_sum="03e0e77821ae6ff4ed5cf49264c23bb0239ef918fc717a3390db782ec801d6d6"
_lib_arm_sum="d771acc10f314906085dc1bcc0995a4abe3262e172f415b6df9c0b7d3f5735a6"
_lib_arm_sig_sum="f2ba81071792fb42b8c3fea4dc2be7d36f60c2100918d0bd1d01c7950acb8bda"
_lib="${_pkg_retroarch}_libretro_android.so"
_evmfs_network="100"
_evmfs_address="0x69470b18f8b8b5f92b48f6199dcb147b4be96571"
# Kid address
_evmfs_ns="0x926acb6aA4790ff678848A9F1C59E578B148C786"
# Dvorak
_evmfs_sig_ns="0x87003Bd6C074C713783df04f36517451fF34CBEf"
_evmfs_dir="evmfs://${_evmfs_network}/${_evmfs_address}/${_evmfs_ns}"
_evmfs_sig_dir="evmfs://${_evmfs_network}/${_evmfs_address}/${_evmfs_sig_ns}"
_arm_evmfs_uri="${_evmfs_dir}/${_lib_arm_sum}"
_arm_evmfs_sig_uri="${_evmfs_sig_dir}/${_lib_arm_sig_sum}"
_aarch64_evmfs_uri="${_evmfs_dir}/${_lib_aarch64_sum}"
_aarch64_evmfs_sig_uri="${_evmfs_sig_dir}/${_lib_aarch64_sig_sum}"
_lib_aarch64_src="${_lib}.aarch64.tar.xz::${_aarch64_evmfs_uri}"
_lib_aarch64_sig_src="${_lib}.aarch64.tar.xz.sig::${_aarch64_evmfs_sig_uri}"
_lib_arm_src="${_lib}.arm.tar.xz::${_arm_evmfs_uri}"
_lib_arm_sig_src="${_lib}.arm.tar.xz.sig::${_arm_evmfs_sig_uri}"
if [[ "${_arch}" == "arm" || \
       "${_arch}" == "armv7l" ]]; then
  _lib_src="${_lib_arm_src}"
  _lib_sig_src="${_lib_arm_sig_src}"
  _lib_sum="${_lib_arm_sum}"
  _lib_sig_sum="${_lib_arm_sig_sum}"
elif [[ "${_arch}" == "aarch64" ]]; then
  _lib_src="${_lib_aarch64_src}"
  _lib_sig_src="${_lib_aarch64_sig_src}"
  _lib_sum="${_lib_aarch64_sum}"
  _lib_sig_sum="${_lib_aarch64_sig_sum}"
fi
source+=(
  "${_lib_src}"
  "${_lib_sig_src}"
)
sha256sums+=(
  "${_lib_sum}"
  "${_lib_sig_sum}"
)
validpgpkeys=(
  # Truocolo
  #   <truocolo@aol.com>
  '97E989E6CF1D2C7F7A41FF9F95684DBE23D6A3E9'
  #   <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
  'F690CBC17BD1F53557290AF51FC17D540D0ADEED'
  # Pellegrino Prevete (dvorak)
  #   <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>
  '12D8E3D7888F741E89F86EE0FEC8567A644F1D16'
)

package() {
  local \
    _dest_dir
  _dest_dir="/data/data/com.retroarch/cores"
  install \
    -dm755 \
    "${pkgdir}${_dest_dir}"
  install \
    -Dm644 \
    "${srcdir}/${_lib}" \
    "${pkgdir}/${_dest_dir}/${_lib}"
}

# vim: ft=sh syn=sh et
