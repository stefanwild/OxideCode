# install bun
curl -fsSL https://bun.sh/install | bash

# check cargo and code versions
cargo --version
code --version

# get code
git clone https://github.com/NxtCore/OxideCode.git
cd OxideCode/vscode-extension

# install modules
bun install

# build native and copy the lib manually
bun run build:native
cp ../target/release/liboxidecode_node.dylib oxidecode.darwin-arm64.node

# build extension and install
bun run build
bun run package
code --install-extension ./*.vsix --force

# restart vscode
code --restart
